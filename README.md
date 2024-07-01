# Speed Vallet

# 🎈 Images 🎈

![Image0](https://github.com/egehan0250/speed-vallet/assets/79449566/5695abc5-bf02-4ea8-ba41-24a6cd11ebf4)

![Image1](https://github.com/egehan0250/speed-vallet/assets/79449566/d40b98df-f686-42d0-b7e6-445a9abf44c9)

# 🔗 Example Create Link 🔗

```js
const vallet = require("speed-vallet");

const data = {
  referer: "localhost", // Referer (Domain: example.com) - REQUIRED
  hash: "xxxx", // API Hash Code  (API Hash Kodu) - REQUIRED
  userName: "xxxx", // API userName (API Kullanıcı Adı) - REQUIRED
  password: "xxxxxxxxxxx", // API password (API Key) - REQUIRED
  shopCode: "xxx", // API Mağaza Kodu - REQUIRED
  productName: "productName", // Ürün Adı - REQUIRED
  productData: "productData", // Ürün Verisi - REQUIRED
  productType: "DIJITAL_URUN", // Ürün Tipi - REQUIRED
  productsTotalPrice: 21, // Ürün Toplam Fiyatı - REQUIRED
  orderPrice: 5.0, // Sipariş Fiyatı - REQUIRED
  currency: "TRY", // Para Birimi - REQUIRED
  orderId: "30", // Sipariş ID - REQUIRED
  locale: "locale", // locale - REQUIRED
  conversationId: "DIJITAL_URUN", // Konuşma ID - REQUIRED
  buyerName: "buyerName", // Alıcı Adı - REQUIRED
  buyerSurName: "buyerSurName", // Alıcı Soyadı - REQUIRED
  buyerGsmNo: "buyerGsmNo", // Alıcı GSM No - REQUIRED
  buyerMail: "buyerEmail@gmail.com", // Alıcı E-Posta - REQUIRED
  buyerIp: "124.432.423", // Alıcı IP - REQUIRED
  buyerAdress: "buyerAdress", // Alıcı Adres
  BuyerCountry: "BuyerCountry", // Alıcı Ülke
  BuyerCity: "BuyerCity", // Alıcı Şehir
  buyerDistrict: "buyerDistrict", // Alıcı İlçe
  callbackOkUrl: "http://localhost/callback/payment/vallet/ok", // Başarılı Ödeme Callback URL - REQUIRED
  callbackFailUrl: "http://localhost/callback/payment/vallet/fail", // Başarısız Ödeme Callback URL - REQUIRED
};

vallet.speedCreatelink(data, (err, res) => {
  if (err) {
    console.log(err);
  } else {
    console.log(res);
  }
});
```

# ✨ Example Express Speed Vallet ✨

```js
const express = require("express");
const app = express();
const vallet = require("speed-vallet");

app.get("/createPaymentLink", (req, res) => {
  const data = {
    referer: "localhost", // Referer (Domain: example.com) - REQUIRED
    hash: "xxxx", // API Hash Code  (API Hash Kodu) - REQUIRED
    userName: "xxxx", // API userName (API Kullanıcı Adı) - REQUIRED
    password: "xxxxxxxxxxx", // API password (API Key) - REQUIRED
    shopCode: "xxx", // API Mağaza Kodu - REQUIRED
    productName: "productName", // Ürün Adı - REQUIRED
    productData: "productData", // Ürün Verisi - REQUIRED
    productType: "DIJITAL_URUN", // Ürün Tipi - REQUIRED
    productsTotalPrice: 21, // Ürün Toplam Fiyatı - REQUIRED
    orderPrice: 5.0, // Sipariş Fiyatı - REQUIRED
    currency: "TRY", // Para Birimi - REQUIRED
    orderId: "30", // Sipariş ID - REQUIRED
    locale: "locale", // locale - REQUIRED
    conversationId: "DIJITAL_URUN", // Konuşma ID - REQUIRED
    buyerName: "buyerName", // Alıcı Adı - REQUIRED
    buyerSurName: "buyerSurName", // Alıcı Soyadı - REQUIRED
    buyerGsmNo: "buyerGsmNo", // Alıcı GSM No - REQUIRED
    buyerMail: "buyerEmail@gmail.com", // Alıcı E-Posta - REQUIRED
    buyerIp: "124.432.423", // Alıcı IP - REQUIRED
    buyerAdress: "buyerAdress", // Alıcı Adres
    BuyerCountry: "BuyerCountry", // Alıcı Ülke
    BuyerCity: "BuyerCity", // Alıcı Şehir
    buyerDistrict: "buyerDistrict", // Alıcı İlçe
    callbackOkUrl: "http://localhost/callback/payment/vallet/ok", // Başarılı Ödeme Callback URL - REQUIRED
    callbackFailUrl: "http://localhost/callback/payment/vallet/fail", // Başarısız Ödeme Callback URL - REQUIRED
  };

  vallet.speedCreatelink(data, (err, res) => {
    if (err) {
      console.log(err);
    } else {
      console.log(res);
    }
  });
});

app.get("/callback/payment/vallet/ok", (req, res) => {
  res.send("Ödeme Başarılı");
});

app.get("/callback/payment/vallet/fail", (req, res) => {
  res.send("Ödeme Başarısız");
});

app.get("/callback/payment/vallet", async (req, res) => {
  let data = {
    status: req.body.status,
    paymentStatus: req.body.paymentStatus,
    hash: req.body.hash,
    paymentAmount: req.body.paymentAmount,
    paymentType: req.body.paymentType,
    conversationId: req.body.conversationId,
    orderId: req.body.orderId,
  };
  if (data.status != "success") return res.send("Ödeme Başarısız");
  res.send("ok");
});

app.listen(3000, () => {
  console.log("Server Started");
});
```

# 🎊 Example Response Speed Vallet 🎊

```js
{
  status: 'success',
  data: {
    status: 'success',
    errorMessage: '',
    payment_page_url: 'https://www.vallet.com.tr/payment-center/en/copay/XXXXXXXXX',
    payment_page_url_domestic_card: 'https://www.vallet.com.tr/payment-center/en/copay/XXXXXXXXX/kredi-karti',
    payment_page_url_bank_transfer_card: 'https://www.vallet.com.tr/payment-center/en/copay/XXXXXXXXX/banka-havale',
    payment_page_url_international_card: 'https://www.vallet.com.tr/payment-center/en/copay/XXXXXXXXX/kredi-karti-dunya',
    ValletOrderNumber: '1111111',
    ValletOrderId: '1111112',
    conversationId: 'DIJITAL_URUN'
  },
  url: 'https://www.vallet.com.tr/payment-center/en/copay/XXXXXXXXX'
}
```

---
- ✨ [For Support](https://github.com/sponsors/egehan0250) <br>
- 💕 [Discord](https://aiuptime.net/discord)<br>
- 🏓 [AIuptime](https://aiuptime.net/)<br>
- ☄️ [Click For Contact](mailto:support@aiuptime.net)<br>

# 🎯 License 🎯
- ⚖️ Its protected by Creative Commons ([CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/))
