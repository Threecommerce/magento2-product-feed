# Changelog

Tutte le modifiche rilevanti a questo modulo sono documentate in questo file.

Il formato è basato su [Keep a Changelog](https://keepachangelog.com/it/1.1.0/)
e questo progetto aderisce al [Semantic Versioning](https://semver.org/lang/it/).

## [1.0.0] - 2026-11-05

### Added
- Feed XML (RSS 2.0 con namespace `g:`) per **Google Merchant Center** e per il **catalogo Meta** (Facebook e Instagram),
  un file per profilo e per store view, in `pub/media/threecommerce_productfeed/`.
- URL con token non indovinabile, derivato dalla chiave di cifratura (stabile nel tempo).
- Generazione da cron (controllo orario, rigenera i file più vecchi di N ore) e dal comando
  `bin/magento threecommerce:productfeed:generate [--store=] [--profile=google|meta]`; il file viene scritto
  su un temporaneo e rinominato a fine lavoro.
- Prezzi dall'indice (speciali, date e regole catalogo già applicati), con IVA come nel negozio;
  `price` + `sale_price` quando c'è uno sconto.
- Filtri: tipi di prodotto, categorie, esclusione per attributo, prodotti esauriti.
- Dati: marca, GTIN, MPN (o SKU), categoria Google, immagini aggiuntive, `product_type` dal percorso categoria,
  `identifier_exists = no` per Google quando mancano GTIN e MPN.
- Configurazione in *Negozi → Configurazione → Threecommerce Plugins → Product Feed*, con gli URL dei feed e lo stato.
