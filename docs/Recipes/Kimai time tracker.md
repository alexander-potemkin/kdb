# Kamai time tracker

- desktop clients: [https://www.kimai.org/store/alexandreptj-kemai-desktop-client.html](https://www.kimai.org/store/alexandreptj-kemai-desktop-client.html)
- templates: [https://www.kimai.org/documentation/invoices.html#create-your-own-invoice-document](https://www.kimai.org/documentation/invoices.html#create-your-own-invoice-document) 
  Cloudron app install has folder created, you just need to upload via Cloudron web interface 

<aside>
💡 Don't restart the Kimai from command prompt under CloudRon - use CloudRon’s restart instead.

</aside>

```bash
cd /app/code/templates/invoice/renderer
cp timesheet.html.twig /app/data/invoices/ #timesheet view
cp default.html.twig /app/data/invoices/  #invoices view
cd /app/data/invoices && ls -l #chown from root if required
```