```js
// from submit filter data added
  const handleSubmitFilter = (data) => {
      const { search, advertiser_id, model, status } = data.data;
      const updatedFilters = { search, advertiser_id, model, status };
      setFilters(Object.fromEntries(Object?.entries(updatedFilters).filter(([_, v]) => v?.length)));
    };
    
```
