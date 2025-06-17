Компонент
```
type TProductCard = {
  title: string;
  origin: string;
  price: number;
  currency: "RUB" | "USD" | "EUR";
  imageUrl: string;
};

const ProductCard = ({
  title,
  origin,
  price,
  currency,
  imageUrl,
}: TProductCard) => {
  const formatCurrency = new Intl.NumberFormat("ru-RU", {
    style: "currency",
    currency: currency,
    minimumFractionDigits: 2,
    maximumFractionDigits: 2,
  }).format(price / 100);

  return (
    <div className="product-card">
      <img className="img-product__card" src={imageUrl} alt="img-product-card" />
      <div>
        <span>{formatCurrency}</span>
        <div className="product-card__title">
          <strong>{title}</strong>
          <span>Происхождение: {origin}</span>
        </div>
      </div>
    </div>
  );
};

export default function App() {
  const card: TProductCard = {
    title: "Робот пылесос",
    origin: "China",
    price: 302343,
    currency: "USD",
    imageUrl: "https://ir.ozone.ru/s3/multimedia-u/wc1000/6629889270.jpg",
  };

  return (
    <div className="app">
      <ProductCard {...card} />
    </div>
  );
}




Стили 

.product-card {
  display: grid;
  grid-template-columns: 1fr 1fr;
  border: 1px solid rgb(71, 71, 71);
  margin: 0 20%;
}
.product-card__title {
  display: flex;
  flex-direction: column;
  margin-block: 10px;
}

.img-product__card {
  width: 100%;
}

@media (max-width: 500px) {
  .product-card {
    grid-template-columns: 1fr;
  }
}
```
