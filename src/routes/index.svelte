

<style>

@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap');

section {
  background: url('images/bg__left.svg') left 10% no-repeat,
    url('images/bg__top-right.svg') right top no-repeat,
    #EFF0F6 url('images/bg__btm-right.svg') right bottom no-repeat;
  font-family: 'Poppins', sans-serif;
  margin: 0;
  padding: 0;
  min-height: 100%;
  min-width: 100%;
}

.wrapper {
  align-items: center;
  display: flex;
  justify-content: center;
  width: 100vw;
  gap: 50px;
  padding: 80px 0;
  height: 100vh;
}

.panel {
  background: white;
  border-radius: 25px;
  box-sizing: border-box;
  box-shadow: 0px 0px 70px #C7CBE3;
  height: 875px;
  padding-top: 50px;
  overflow-y: scroll;
  width: 375px;
}

h1 {
  padding-left: 40px;
  font-size: 2rem;
  font-weight: bold;
  padding-bottom: 20px;
}

ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

ul.menu li {
  margin-left: 15px;
  display: flex;
  padding-right: 30px;
  position: relative;
  gap: 20px;
  margin-bottom: 45px;
}

ul.menu li:nth-child(4n + 1):before {
  --background: #e1f1fe
}

ul.menu li:nth-child(4n + 2):before {
  --background: #ffe2f0
}

ul.menu li:nth-child(4n + 3):before {
  --background: #f7f7fe
}

ul.menu li:nth-child(4n + 4):before {
  --background: #defef0
}

ul.menu li:before {
  background: var(--background);
  border-bottom-left-radius: 20px;
  border-top-left-radius: 20px;
  content: '';
  display: block;
  width: 100%;
  height: 100%;
  position: absolute;
  left: 30px;
  top: 0;
  z-index: 1;
}

ul.menu .plate {
  height: 148px;
  width: 148px;
  position: relative;
  z-index: 2;
  top: -15px;
}

ul.menu .content {
  padding-top: 30px;
  position: relative;
  width: 100%;
  z-index: 3;
}

.menu-item {
  font-size: 1.125rem;
  line-height: 20px;
  margin: 0 0 16px 0;
  padding: 0;
}

.price,
.subtotal{
  font-size: 2rem;
  line-height: 1;
  font-weight: bold;
}

ul.menu .price {
  margin: 0 0 20px 0;
  padding: 0;
}

button {
  background: #6B00F5;
  border: none;
  cursor: pointer;
  font-family: 'Poppins', sans-serif;
  border-radius: 20px;
  padding: 4px 18px;
  font-size: 1rem;
  color: white;
  font-weight: bold;
  line-height: 1.2;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}

ul.menu button {
  position: absolute;
}

button.in-cart {
  background: black;
}

.cart p.empty {
  padding-left: 40px;
}

.cart-summary {
  border-bottom: 5px solid #D7D7F9;
  margin: 0 30px 0 25px;
}

.cart-summary li {
  display: grid;
  grid-template-areas: "plate content content"
    "plate quantity price";
}

.cart-summary .menu-item {
  margin-bottom: 5px;
}

.cart-summary p {
  margin-bottom: 0;
}

.cart-summary .price {
  margin: 0 0 16px 0;
  font-size: 1rem;
}

.cart .plate {
  position: relative;
  height: 64px;
  width: 64px;
  display: flex;
  align-items: center;
  justify-content: center;
  grid-area: plate;
}

.cart .plate img {
  height: 64px;
  width: 64px;
  position: absolute;
  left: 0;
  top: 0;
  z-index: 1;
}

.cart-summary .content {
  grid-area: content;
}

.cart .quantity {
  background: black;
  color: white;
  font-size: 1rem;
  grid-area: quantity;
  font-weight: bold;
  border-radius: 50%;
  height: 32px;
  width: 32px;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2;
}

.quantity__wrapper {
  display: flex;
  gap: 10px;
}

.quantity__wrapper .quantity {
  background: none;
  color: black;
}

.decrease,
.increase {
  padding: 0;
  height: 32px;
  width: 32px;
  display: block;
}

.decrease:hover,
.increase:hover {
  background: black;
}

.decrease img {
  top: 1px;
  position: relative;
  left: -1px;
}

.increase img {
  transform: rotate(180deg);
  position: relative;
  top: 1px;
  left: 2px;
}

.cart-summary li {
  border-bottom: 1px solid #D7D7F9;
  margin-bottom: 45px;
  padding-bottom: 45px;
}

.cart-summary li:last-child {
  border-bottom: 0;
  padding-bottom: 0;
}

.cart-summary li .subtotal {
  text-align: right;
}

.totals {
  padding: 35px 30px;
}

.line-item {
  display: flex;
  align-items: flex-end;
  text-align: right;
  margin-bottom: 20px;
}

.line-item .label {
  font-size: 1rem;
  font-weight: bold;
  width: 60%;
}

.line-item .amount {
  width: 40%;
}

.line-item.total .price {
  color: #6B00F5;
}

</style>

<script>
  import { centsToDollars } from '../utils'
  const items = [
    {
        name: 'French Fries with Ketchup',
        price: 223,
        image: 'plate__french-fries.png',
        alt: 'French Fries',
        count: 0
    },
    {
        name: 'Salmon and Vegetables',
        price: 512,
        image: 'plate__salmon-vegetables.png',
        alt: 'Salmon and Vegetables',
        count: 0
    },
    {
        name: 'Spaghetti Meat Sauce',
        price: 782,
        image: 'plate__spaghetti-meat-sauce.png',
        alt: 'Spaghetti with Meat Sauce',
        count: 0
    },
    {
        name: 'Bacon, Eggs, and Toast',
        price: 599,
        image: 'plate__bacon-eggs.png',
        alt: 'Bacon, Eggs, and Toast',
        count: 0
    },
    {
        name: 'Chicken Salad with Parmesan',
        price: 698,
        image: 'plate__chicken-salad.png',
        alt: 'Chicken Salad with Parmesan',
        count: 0
    },
    {
        name: 'Fish Sticks and Fries',
        price: 634,
        image: 'plate__fish-sticks-fries.png',
        alt: 'Fish Sticks and Fries',
        count: 0
    }
  ]

  $: menuItems = items

  $: cartItems = menuItems.filter((item) => item.count > 0)

  $: subtotal = cartItems.map((item) => item.price * item.count).reduce(add, 0)

  $: tax = calculateTax(subtotal)

  function add(accumulator, a) {
    return accumulator + a;
  }
    
  function calculateTax(sub) {
    var salesTax = .10
    return sub * (1 + salesTax)
  }

  function addToCart(index) {
    let item = menuItems[index]

    if (item.count > 0) {

      item = {
        ...item,
        count: item.count + 1,
      }
    }

    menuItems[index] = { ...item, count: 1 }
  }

  function incrementCount(item) {
    const itemIndex = menuItems.findIndex(i => i.name === item.name)
    item.count = item.count + 1

  
    menuItems[itemIndex] = item
  }

  function decrementCount(item) {
    const itemIndex = menuItems.findIndex(i => i.name === item.name)

    if (item.count === 0) return menuItems[itemIndex] = item

    item.count = item.count - 1

    menuItems[itemIndex] = item
  }

</script>


<section>


  <div class="wrapper menu">
    <div class="panel">
      <h1>To Go Menu</h1>
      <ul class="menu">
      
        {#each menuItems as item, i}
          <li>
            <div class="plate">
            <img src={`images/${item.image}`} alt={item.alt} class="plate" />
          </div>
          <div class="content">
            <p class="menu-item">{item.name}</p>
            <p class="price">{centsToDollars(item.price)}</p>
            {#if item.count > 0}
              <button class='in-cart'>
              <img src="images/check.svg" alt="Check" />
              In Cart
            </button>
           {:else}
            <button class="add" on:click={() => addToCart(i)}>Add to Cart</button>
           {/if}
          </div>
          </li>
        {/each}
        
      </ul>
    </div>

    <div class="panel cart">
      <h1>Your Cart</h1>
      {#if !cartItems.length}
        <p class="empty">Your cart is empty.</p>
      {/if}

      <ul class="cart-summary">

        {#each cartItems as item, i}
          <li>
            <div class="plate">
              <img src="images/plate__fish-sticks-fries.png" alt="Fish Sticks and Fries" class="plate" />
              <div class="quantity">{item.count}</div>
            </div>
            <div class="content">
              <p class="menu-item">{item.name}</p>
              <p class="price">{centsToDollars(item.price)}</p>
            </div>
            <div class="quantity__wrapper">
              <button class="decrease" on:click={() => decrementCount(item)}>
                <img src="images/chevron.svg" alt='Decrease' />
              </button>
              <div class="quantity">{item.count}</div>
              <button class="increase" on:click={() => incrementCount(item)}>
                <img src="images/chevron.svg" alt='Increase' />
              </button>
            </div>
            <div class="subtotal">
              {centsToDollars(item.price * item.count)}
            </div>
          </li>
        {/each}
      </ul>

      <div class="totals">
        <div class="line-item">
          <div class="label">Subtotal:</div>
          <div class="amount price subtotal">{centsToDollars(subtotal)}</div>
        </div>
        <div class="line-item">
          <div class="label">Tax:</div>
          <div class="amount price tax">{centsToDollars(tax)}</div>
        </div>
        <div class="line-item total">
          <div class="label">Total:</div>
          <div class="amount price total">{centsToDollars(subtotal + tax)}</div>
        </div>
      </div>
    </div>
  </div>

</section>