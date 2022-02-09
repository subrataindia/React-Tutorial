# React-Tutorial

## react-router-dom v6

~~~javascript
import Header from './Header';
import Nav from './Nav';
import Footer from './Footer';
import Home from './Home';
import NewPost from './NewPost';
import PostPage from './PostPage';
import About from './About';
import Missing from './Missing';

import {BrowserRouter as Router, Route, Routes} from 'react-router-dom';

function App() {
  return (
    <div className="App">
      <Router>
        <Header/>
        <Nav/>
        <Routes>
          <Route exact path="/" element={<Home />} />
          <Route exact path="/about" element={<About />} />
          <Route exact path="/post" element={<NewPost />} />
          <Route exact path="/post/:id" element={<PostPage />} />
          <Route exact path="*" element={<Missing />} />
        </Routes>
        <Footer/>
      </Router>  
    </div>
  );
}

export default App;
~~~

## NAV 

~~~javascript
import {Link} from 'react-router-dom';

const Nav = ({search, setSearch}) => {
  return (
    <nav className='Nav'>
      <form className='searchForm' onSubmit={(e) => e.preventDefault()}>
        <label htmlFor='searchForm'>Search Form</label>
        <input
          id="searchForm"
          type="text"
          placeholder='Search Form'
          value={search}
          onChange={(e) => setSearch(e.target.value)}
          />
      </form>
      <ul>
        <li><Link to="/">Home</Link></li>
        <li><Link to="/post">Post</Link></li>
        <li><Link to="/about">About</Link></li>
      </ul>
    </nav>
  );
};

export default Nav;
~~~

## Filter posts as per search

~~~javascript
  useEffect(() =>{
    const filteredResults = posts.filter(post => ((post.body).toLowerCase()).includes(search.toLowerCase))
  },[posts, search])
~~~
