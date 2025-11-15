let books = [
  {id: 1, title: "js books", author: "des", price: 100, stocks: 10},
  {id: 2, title: "python books", author: "des", price: 100, stocks: 10},
  {id: 3, title: "html books", author: "john", price: 120, stocks: 5},
  {id: 4, title: "css books", author: "mary", price: 80, stocks: 15},
  {id: 5, title: "nodejs books", author: "alex", price: 150, stocks: 8}
];

const cart = [];
let total = 0;

function browseBooks() {
  console.log("Browsing Books:");
  books.forEach(book => {
    console.log(`${book.id}. ${book.title} by ${book.author} - $${book.price} (Stock: ${book.stocks})`);
  });
}

function addToCart(bookId) {
  const book = books.find(b => b.id === bookId);
  if (book && book.stocks > 0) {
    const existingItem = cart.find(item => item.id === bookId);
    if (existingItem) {
      existingItem.quantity += 1;
    } else {
      cart.push({ ...book, quantity: 1 });
    }
    book.stocks -= 1;
    total += book.price;
    console.log(`Added "${book.title}" to your cart.`);
  } else {
    console.log("Sorry, this book is out of stock.");
  }
}

function showCart() {
  if (cart.length === 0) {
    console.log("Your cart is empty.");
  } else {
    console.log("Your Cart:");
    cart.forEach(item => {
      console.log(`${item.title} - $${item.price} x ${item.quantity}`);
    });
    console.log(`Total: $${total}`);
  }
}

function checkout() {
  if (cart.length === 0) {
    console.log("Your cart is empty. Please add items to your cart.");
  } else {
    console.log("Thank you for your purchase!");
    console.log(`Total amount: $${total}`);
    // Reset cart after checkout
    cart.length = 0;
    total = 0;
  }
}



console.log("Welcome!!! Customer");
browseBooks();

addToCart(1); 
addToCart(3); 
addToCart(5); 


showCart();

checkout();


showCart();
