```js
// from submit filter data added
  const handleSubmitFilter = (data) => {
      const { search, advertiser_id, model, status } = data.data;
      const updatedFilters = { search, advertiser_id, model, status };
      setFilters(Object.fromEntries(Object?.entries(updatedFilters).filter(([_, v]) => v?.length)));
    };
    
```


```js
useEffect(() => {
  const fetchDeposits = async () => {
    setLoading(true);
  
    try {
      const params = new URLSearchParams({
        page: page.toString(),
        search: search || "",
        provider: provider || "",
        payment_method: payment_method || "",
      });

      const { data } = await useApi.get(`/admin/deposit/all?${params.toString()}`);
      
      setDeposit(data?.data?.data || []);
    } catch (error) {
      console.error('Error fetching deposits:', error);
    } finally {
      setLoading(false);
    }
  };

  fetchDeposits();
  
}, [page, search, provider, payment_method, filterItems]);
```

```js
useEffect(() => {
    const fetchDeposits = async () => {
        try {
            setLoading(true); 
            
            const params = new URLSearchParams({
                page: page.toString(),
            });

            if (search) params.append('search', search);
            if (payment_gateway) params.append('provider', payment_gateway);
            if (payment_method) params.append('payment_method', payment_method);


            const { data } = await useApi.get(`/admin/deposit/all?${params.toString()}`);

            setDeposit(data?.data?.data || []); 
        } catch (error) {
            console.error('Error fetching deposits:', error);
        } finally {
            setLoading(false); 
        }
    };

    fetchDeposits();
}, [page, search, payment_gateway, payment_method]);
```
