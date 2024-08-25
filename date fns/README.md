<p>
 <h1 style="color:red;" align="center">Date-fns</h1>
</p>



```sh
npm i date-fns
```

```js
import { format } from 'date-fns';
format(new Date(), 'dd/MM/yyyy')
//  21/11/2023
format(new Date(), 'PP')
// Nov 21, 2023
```

```js
import { formatDistance } from 'date-fns'
//What is the distance between 2 July 2014 and 1 January 2015?
const result = formatDistance(new Date(2014, 6, 2), new Date(2015, 0, 1))
//=> '6 months'

//example project
const totaldays = parseInt(formatDistance(new Date(room?.to), new Date(room?.from)).split(' ')[0])
const totalprice=totaldays * room?.price
console.log(totalprice)
```

```js
npm install lodash
import { debounce } from "lodash";
 // Debounced search state and functionlity
  const [debouncedSearch, setDebouncedSearch] = useState(search);
  useEffect(() => {
    const handler = debounce(() => setDebouncedSearch(search), 500);
    handler();
    return () => handler.cancel();
  }, [search]);
```

