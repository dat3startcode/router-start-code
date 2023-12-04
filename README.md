# Code Snippets meant for a React Router Exercise

### 1) Add the following to index.css (leave styles for body)
```
ul.header {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: #333;
 }
 
 ul.header li { float: left;}
 
 ul.header li a {
  display: block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
 }
 ul.header li a:hover:not(.active) { background-color: #111;}
 .active { background-color: #4CAF50;}
 
 ```
 ### 2) Create a new file bookFacade.js and add the following content to the file
  ```
 function bookFacade() {
  let books = [
      { id: 100,title: "How to Learn JavaScript - Vol 1", info: "Study hard"},
      { id: 101,title: "How to Learn ES6", info: "Complete all exercises :-)"},
      { id: 102,title: "How to Learn React",info: "Complete all your CA's"},
      { id: 103,title: "Learn React", info: "Don't drink beer(s), until Friday (after four)"
      }
    ]
  let nextId = 104;  
  const getBooks = () => { return books}
  const findBook = (id) => {
    const bookId = isNaN(id) ? id : Number(id);
    return books.find(book=>book.id===bookId)
  }
  const deleteBook = (id) => {    
    const bookId = isNaN(id) ? Number(id) : id;
     books = books.filter(book=>book.id!==bookId)
  }
  const addBook = (book) => {
    book.id = nextId
    books.push(book)
    nextId++;
  }

  return {
    // Remember all statements below are a shortcut for this version: getBooks: getBooks
    getBooks,
    findBook,
    deleteBook,
    addBook,
  }
}

let returnVal =  bookFacade()
export default returnVal;
 ```
 ### 3) In main.js setup App with bookFacade:
```
import { 
RouterProvider, 
createBrowserRouter,
createRoutesFromElements,
Route, } from 'react-router-dom'

const router = createBrowserRouter(createRoutesFromElements(
  <Route path="/" element={<App bookFacade={bookFacade}/>} />
    
));

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <RouterProvider router={router} />
  </React.StrictMode>,
)
 ``` 
### Don't continue before you know exactly what happens in the code given in 2+3 (observe how the `bookFacade` is passed into `App` as props)
