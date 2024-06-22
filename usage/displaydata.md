---
layout: default
title: Displaying Data
---

# Displaying Data

Here's a rundown on a simple way to get our data.

First, grab the JSON files and compile them:

```

document.addEventListener('DOMContentLoaded', function() {
    // List of known JSON file URLs
    const jsonUrls = [
      //'https://botanybase.github.io/data/plants.json',  <-- Old JSON DB File
      'https://botanybase.github.io/data/tropical.json',
      'https://botanybase.github.io/data/subtropical.json',
      'https://botanybase.github.io/data/temperate.json',
      'https://botanybase.github.io/data/alpine.json',
      'https://botanybase.github.io/data/desert.json'
      // Add more URLs as needed
    ];

    async function fetchAndCombineJSON(urls) {
      const fetchPromises = urls.map(url => fetch(url).then(response => response.json()));
      try {
        const jsonArrays = await Promise.all(fetchPromises);
        const combinedArray = jsonArrays.flat();
        return combinedArray;
      } catch (error) {
        console.error('Error fetching JSON files:', error);
        return [];
      }
    }

```

Now, filter entries:

```

fetchAndCombineJSON(jsonUrls).then(combinedData => {
      displayPlants(combinedData);
    });

    function displayPlants(plants) {
      const plantEntriesContainer = document.querySelector('.plant-entries');
      const searchInput = document.querySelector('#search-input');
      const message = document.createElement('p');
      message.textContent = 'Start typing, or enter * to show all plants';
      plantEntriesContainer.appendChild(message);

      searchInput.addEventListener('input', () => {
        const searchQuery = searchInput.value.toLowerCase();
        let filtered = [];

        if (searchQuery === '') {
          plantEntriesContainer.innerHTML = '';
          plantEntriesContainer.appendChild(message);
        } else if (searchQuery === '*') {
          filtered = plants;
        } else {
          filtered = plants.filter(plant => {
            const plantName = plant.name.toLowerCase();
            const plantDescription = plant.description.toLowerCase();
            return plantName.includes(searchQuery) || plantDescription.includes(searchQuery);
          });
        }

```

Then, if you want to, add a message when the search field is empty

```

plantEntriesContainer.innerHTML = ''; // Clear previous entries

        if (filtered.length === 0) {
          const noResultsMessage = document.createElement('p');
          noResultsMessage.textContent = 'No results, try a different query';
          plantEntriesContainer.appendChild(noResultsMessage);
        } else {

```

After that, define a entry HTML:

```

filtered.forEach(plant => {
            const plantEntryHTML = `
              <div class="entry-wrapper">
                <h2>${plant.name}</h2>
                <small><p style="text-align: center;">${plant.climate}</p></small>
                <p>${plant.description}</p>
                <div style="text-align: center;">
                <p style="color: #ffffff;">${plant.height}</p>
                <p style="color: #ffffff;">${plant.special_feature}</p>
                </div>
                <a href="#${plant.name.replace(/\s+/g,'-')}" rel="modal:open">
                  <img src="${plant.image}" alt="${plant.name}">
                </a>
              </div>

              <div id="${plant.name.replace(/\s+/g,'-')}" class="modal">
              <p>Image:</p>
              <img src="${plant.image}" alt="plant.name">
              <a href="#" rel="modal:close">Close</a>
              </div>
            `;
            const plantEntryElement = document.createElement('div');
            plantEntryElement.innerHTML = plantEntryHTML;
            plantEntriesContainer.appendChild(plantEntryElement);
          });
        }
      });
    }
  });

```


You're all done! Do edit and modify to suit your needs!
