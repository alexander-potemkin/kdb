# GitHub Pages config


1. Go to your repository (and keep in mind it shall be public or paid) - at Settings → Pages
2. Enable them and add the domain name desired
3. Create 4 `A` records on your DNS provider, pointing `@` to 

185.199.111.153
185.199.110.153
185.199.109.153
185.199.108.153

Which is 185.199.[108-111].153

If it's not a root domain, a CNAME record is recommended by GitHub (it will advice on the record, once DNS name entered).