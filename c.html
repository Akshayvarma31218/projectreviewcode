
{
  "name": "handloom-heritage",
  "version": "1.0.0",
  "private": true,
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.14.1"
  },
  "devDependencies": {
    "vite": "^5.0.0"
  },
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  }
}

/* src/main.jsx */
import React from 'react'
import { createRoot } from 'react-dom/client'
import { BrowserRouter } from 'react-router-dom'
import App from './App'
import { StoreProvider } from './context/StoreContext'
import './style.css'

createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <BrowserRouter>
      <StoreProvider>
        <App />
      </StoreProvider>
    </BrowserRouter>
  </React.StrictMode>
)

/* src/App.jsx */
import React from 'react'
import { Routes, Route } from 'react-router-dom'
import Header from './components/Header'
import Footer from './components/Footer'
import Home from './pages/Home'
import ProductPage from './pages/ProductPage'
import CartModal from './components/CartModal'
import { useStore } from './context/StoreContext'

export default function App() {
  const { state } = useStore()

  return (
    <div className="app-root">
      <Header />

      <main>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/product/:id" element={<ProductPage />} />
        </Routes>
      </main>

      {state.ui.showCart && <CartModal />}

      <Footer />
    </div>
  )
}

/* src/context/StoreContext.jsx */
import React, { createContext, useContext, useReducer } from 'react'

const StoreContext = createContext()

const initialState = {
  products: [],
  cart: [],
  ui: { showCart: false },
  filters: { categories: [], minPrice: 0, maxPrice: 50000 }
}

function reducer(state, action) {
  switch (action.type) {
    case 'SET_PRODUCTS':
      return { ...state, products: action.payload }
    case 'ADD_TO_CART':
      return { ...state, cart: [...state.cart, action.payload] }
    case 'REMOVE_FROM_CART':
      return { ...state, cart: state.cart.filter((_, i) => i !== action.payload) }
    case 'TOGGLE_CART':
      return { ...state, ui: { ...state.ui, showCart: action.payload } }
    case 'SET_FILTERS':
      return { ...state, filters: { ...state.filters, ...action.payload } }
    default:
      return state
  }
}

export function StoreProvider({ children }) {
  const [state, dispatch] = useReducer(reducer, initialState)

  const value = { state, dispatch }
  return <StoreContext.Provider value={value}>{children}</StoreContext.Provider>
}

export function useStore() {
  const ctx = useContext(StoreContext)
  if (!ctx) throw new Error('useStore must be used inside StoreProvider')
  return ctx
}

/* src/api/products.js (mock API) */
export function fetchProducts() {
  // simulate network latency and return promise
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve([
        {
          id: '1',
          name: 'Traditional Kanchipuram Silk Saree',
          category: 'SAREES',
          price: 12500,
          originalPrice: 15000,
          image: '/images/saree-kanchipuram.jpg',
          rating: 4.5,
          reviews: 124,
          handmade: true
        },
        {
          id: '2',
          name: 'Traditional White Cotton Kurta',
          category: "MEN'S KURTAS",
          price: 3500,
          originalPrice: 4200,
          image: '/images/men-kurta-white.jpg',
          rating: 5,
          reviews: 89,
          handmade: false
        },
        {
          id: '3',
          name: 'Handwoven Silk Dupatta',
          category: 'DUPATTAS',
          price: 2200,
          originalPrice: 2800,
          image: '/images/silk-dupatta.jpg',
          rating: 4.2,
          reviews: 112,
          handmade: true
        }
      ])
    }, 700)
  })
}

/* src/hooks/useFetch.js */
import { useState, useEffect } from 'react'

export function useFetch(fetcher) {
  const [data, setData] = useState(null)
  const [loading, setLoading] = useState(true)
  const [error, setError] = useState(null)

  useEffect(() => {
    let mounted = true
    setLoading(true)
    fetcher()
      .then((res) => {
        if (!mounted) return
        setData(res)
      })
      .catch((err) => {
        if (!mounted) return
        setError(err)
      })
      .finally(() => mounted && setLoading(false))

    return () => (mounted = false)
  }, [fetcher])

  return { data, loading, error }
}

/* src/pages/Home.jsx */
import React, { useEffect } from 'react'
import { useStore } from '../context/StoreContext'
import { fetchProducts } from '../api/products'
import ProductList from '../components/ProductList'

export default function Home() {
  const { state, dispatch } = useStore()

  useEffect(() => {
    let mounted = true
    fetchProducts().then((list) => {
      if (!mounted) return
      dispatch({ type: 'SET_PRODUCTS', payload: list })
    })
    return () => (mounted = false)
  }, [dispatch])

  return (
    <div className="home-page">
      <section className="hero-section" style={{ backgroundImage: "url('/images/banner-bg.jpg')" }}>
        <div className="hero-overlay">
          <div className="hero-content">
            <h2>Handloom Heritage</h2>
            <p>Discover authentic Indian handloom products crafted with traditional techniques.</p>
          </div>
        </div>
      </section>

      <div className="product-page-container">
        <aside className="filter-sidebar">
          <h3>Categories</h3>
          {/* simple category filters - update state with dispatch */}
          <div className="filter-group category-filter">
            <label>
              <input
                type="checkbox"
                onChange={(e) => {
                  // example: toggle "SAREES" category in filters
                  const cat = 'SAREES'
                  const has = state.filters.categories.includes(cat)
                  dispatch({
                    type: 'SET_FILTERS',
                    payload: { categories: has ? state.filters.categories.filter(c => c!==cat) : [...state.filters.categories, cat] }
                  })
                }}
              />{' '}
              Sarees
            </label>
          </div>

          <hr />
          <h3>Price Range</h3>
          <div className="filter-group price-filter">
            <input
              type="range"
              min="0"
              max="50000"
              value={state.filters.maxPrice}
              onChange={(e) => dispatch({ type: 'SET_FILTERS', payload: { maxPrice: Number(e.target.value) } })}
            />
            <div>Up to ₹{state.filters.maxPrice}</div>
          </div>

          <button onClick={() => dispatch({ type: 'TOGGLE_CART', payload: true })} className="apply-filters-btn">Open Cart</button>
        </aside>

        <ProductList products={state.products} />
      </div>
    </div>
  )
}


import React from 'react'
import { useParams } from 'react-router-dom'
import { useStore } from '../context/StoreContext'

export default function ProductPage() {
  const { id } = useParams()
  const { state, dispatch } = useStore()
  const product = state.products.find((p) => p.id === id)

  if (!product) return <div className="container">Product not found</div>

  return (
    <div className="product-page container">
      <div className="product-detail">
        <img src={product.image} alt={product.name} />
        <div className="info">
          <h2>{product.name}</h2>
          <p>Category: {product.category}</p>
          <p>Price: ₹{product.price}</p>
          <button onClick={() => dispatch({ type: 'ADD_TO_CART', payload: product })}>Add to Cart</button>
        </div>
      </div>
    </div>
  )
}


import React from 'react'
import { Link } from 'react-router-dom'
import { useStore } from '../context/StoreContext'

export default function Header() {
  const { state, dispatch } = useStore()

  return (
    <header className="main-header">
      <div className="top-bar">
        <Link to="/" className="logo">Handloom Heritage</Link>

        <div className="search-container">
          <input type="search" placeholder="Search handloom products..." className="search-input" />
          <button className="search-button">🔍</button>
        </div>

        <div className="user-actions">
          <button className="account-btn">👤</button>
          <button className="cart-btn" onClick={() => dispatch({ type: 'TOGGLE_CART', payload: true })}>
            🛒 <span className="cart-count">({state.cart.length})</span>
          </button>
        </div>
      </div>

      <nav className="main-navigation">
        <ul className="nav-list">
          <li><Link to="/" className="nav-item">All Products</Link></li>
          <li><Link to="/">Sarees</Link></li>
          <li><Link to="/">Dresses</Link></li>
        </ul>
      </nav>
    </header>
  )
}
import React from 'react'
import ProductCard from './ProductCard'

export default function ProductList({ products = [] }) {
  if (!products.length) return <div className="product-grid empty">Loading products...</div>

  return (
    <section className="product-listing">
      <div className="listing-header">
        <h2>Our Collection</h2>
        <p className="product-count">{products.length} products found</p>
      </div>

      <div className="product-grid">
        {products.map((p) => (
          <ProductCard key={p.id} product={p} />
        ))}
      </div>
    </section>
  )
}

import React from 'react'
import { Link } from 'react-router-dom'
import { useStore } from '../context/StoreContext'

export default function ProductCard({ product }) {
  const { dispatch } = useStore()

  return (
    <article className="product-card">
      <div className="product-image-wrapper">
        <Link to={`/product/${product.id}`}>
          <img src={product.image} alt={product.name} />
        </Link>
        {product.handmade && <span className="badge badge-handmade">Handmade</span>}
      </div>

      <div className="product-info">
        <h4 className="product-category">{product.category}</h4>
        <p className="product-name">{product.name}</p>
        <div className="rating-display">
          <span className="stars">{'★'.repeat(Math.round(product.rating))}</span>
          <span className="review-count">({product.reviews})</span>
        </div>
        <div className="price-box">
          <span className="current-price">₹{product.price}</span>
          {product.originalPrice && <span className="original-price">₹{product.originalPrice}</span>}
        </div>
        <div className="card-actions">
          <button className="add-to-cart-btn" onClick={() => dispatch({ type: 'ADD_TO_CART', payload: product })}>🛒 Add to Cart</button>
          <button className="wishlist-btn">🤍</button>
        </div>
      </div>
    </article>
  )
}

import React from 'react'
import { useStore } from '../context/StoreContext'

export default function CartModal() {
  const { state, dispatch } = useStore()

  return (
    <div className="shopping-cart-modal">
      <div className="modal-content">
        <header className="modal-header">
          <h3>Shopping Cart</h3>
          <button className="close-btn" onClick={() => dispatch({ type: 'TOGGLE_CART', payload: false })}>×</button>
        </header>

        <div className="cart-body">
          {state.cart.length === 0 ? (
            <div className="empty-cart-message">
              <span className="cart-icon">🛍️</span>
              <p>Your cart is empty</p>
              <p className="sub-text">Add some beautiful handloom products!</p>
            </div>
          ) : (
            <ul className="cart-items">
              {state.cart.map((item, idx) => (
                <li key={idx} className="cart-item">
                  <img src={item.image} alt="" />
                  <div className="meta">
                    <div>{item.name}</div>
                    <div>₹{item.price}</div>
                  </div>
                  <button onClick={() => dispatch({ type: 'REMOVE_FROM_CART', payload: idx })}>Remove</button>
                </li>
              ))}
            </ul>
          )}
        </div>

        <footer className="cart-footer">
          <div className="cart-summary">
            <div>Total: ₹{state.cart.reduce((s, it) => s + it.price, 0)}</div>
            <button className="checkout-btn">Checkout</button>
          </div>
        </footer>
      </div>
    </div>
  )
}

/
import React from 'react'

export default function Footer() {
  return (
    <footer className="main-footer">
      <div className="footer-bottom">
        <p>© 2025 Handloom Heritage. All rights reserved.</p>
      </div>
    </footer>
  )
}

/* src/style.css (simplified; paste your original CSS and tweak) */
:root {
  --accent: #b72e2e;
  --muted: #777;
}
body { font-family: Inter, system-ui, Arial; margin: 0; color: #222 }
a { text-decoration: none; color: inherit }
.app-root { min-height: 100vh; display: flex; flex-direction: column }
.main-header { background: #fff; border-bottom: 1px solid #eee; }
.top-bar { display:flex; gap:1rem; align-items:center; padding:12px 20px; justify-content:space-between }
.logo { font-weight:700; font-size:1.25rem }
.search-input { padding:8px 10px; border-radius:6px; border:1px solid #ddd }
.main-navigation { background:#fafafa; padding:8px 20px }
.nav-list { display:flex; gap:12px; list-style:none; padding:0; margin:0 }
.hero-section { height:260px; background-size:cover; background-position:center }
.hero-overlay { background:linear-gradient(180deg, rgba(0,0,0,0.2), rgba(0,0,0,0.2)); height:100%; display:flex; align-items:center }
.hero-content { color:#fff; padding:20px }
.product-page-container { display:flex; gap:20px; padding:20px }
.filter-sidebar { width:260px; background:#fff; border-radius:8px; padding:16px; box-shadow:0 2px 6px rgba(0,0,0,0.04) }
.product-listing { flex:1 }
.product-grid { display:grid; grid-template-columns:repeat(auto-fill, minmax(240px,1fr)); gap:16px }
.product-card { background:#fff; border-radius:8px; overflow:hidden; box-shadow:0 6px 18px rgba(0,0,0,0.03) }
.product-image-wrapper img { width:100%; height:180px; object-fit:cover }
.product-info { padding:12px }
.add-to-cart-btn { background:var(--accent); color:#fff; border:none; padding:8px 12px; border-radius:6px }
.shopping-cart-modal { position:fixed; right:20px; top:60px; width:360px; z-index:50 }
.modal-content { background:#fff; border-radius:8px; box-shadow:0 6px 30px rgba(0,0,0,0.15); overflow:hidden }
.cart-body { padding:12px }

@media (max-width:900px) {
  .product-page-container { flex-direction:column }
  .filter-sidebar { width:100% }
}

/* README instructions (git + deploy) */
/** README (short)

1) Initialize project and paste files
   - npm create vite@latest handloom-heritage --template react
   - npm install
   - Replace src/ files with the ones above

2) Run locally
   - npm run dev

3) Git
   - git init
   - git add .
   - git commit -m "Initial React app - Handloom Heritage"
   - Create GitHub repo and push

4) Deploy
   - Option A: Vercel — import GitHub repo (automatic)
   - Option B: Netlify — connect repo, build command: npm run build, publish: dist

