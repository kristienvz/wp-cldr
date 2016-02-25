# wp-cldr

This plugin provides WordPress developers with easy access to localized country/region names, language names, currency names/symbols/usage, and other localization info from the [Unicode Common Locale Data Repository (CLDR)] (http://cldr.unicode.org/).

With the plugin active, WordPress developers will have access across nearly 100 WordPress locales to localized data items including:
- localized names for territories including ISO 3166 country codes and UN M.49 region codes
- localized currency names and symbols for ISO 4317 currency codes
- information on currency usage in different countries
- localized language names for ISO 639 language codes
- localized calendar information including the first day of the week in different countries
- telephone codes for different countries

The plugin includes support for high volume application. It includes two layers of caching (in-memory arrays and the WordPress object cache). It is currently used on WordPress.com.

CLDR is a library of localization data managed by Unicode. It emphasizes [common, everyday usage] (http://cldr.unicode.org/translation/country-names) and is available in over 700 language-region locales. It is [updated every six months] (http://cldr.unicode.org/index/downloads) and used by [all major software systems] (http://cldr.unicode.org/#TOC-Who-uses-CLDR-). CLDR data is licensed under [Unicode's data files and software license] (http://unicode.org/copyright.html#Exhibit1) which is on [the list of approved GPLv2 compatible licenses] (https://www.gnu.org/philosophy/license-list.html#Unicode).

The plugin currently includes CLDR data for WordPress.org locales including aa, ae, af, ak, am, an, ar, arq, ary, as, ast, av, ay, az, azb, az_TR, ba, bal, bcc, bel, bg_BG, bh, bi, bm, bn_BD, bo, bre, bs_BA, ca, ce,ceb, ch, ckb, co, cr, cs_CZ, csb, cu, cv, cy, da_DK, de_DE, de_CH, dv, dzo, ee, el-po, el, art_xemoji, en_US, en_AU, en_CA, en_GB, en_NZ, en_ZA, eo, es_ES, es_AR, es_CL, es_CO, es_GT, es_MX, es_PE, es_PR, es_VE, et, eu, fa_IR, fa_AF, fuc, fi, fj, fo, fr_FR, fr_BE, fr_CA, fr-ch, frp, fur, fy, ga, gd, gl_ES, gn, gsw, gu, ha, haw_US, haz, he_IL, hi_IN, hr, hu_HU, hy, ia, id_ID, ido, ike, ilo, is_IS, it_IT, ja, jv_ID, ka_GE, kab, kal, kin, kk, km, kmr, kn, ko_KR, ks, ky_KY, la, lb_LU, li, lin, lo, lt_LT, lv, me_ME, mg_MG, mhr, mk_MK, ml_IN, mn, mr, mri, mrj, ms_MY, mwl, my_MM, ne_NP, nb_NO, nl_NL, nl_BE, nn_NO, no, oci, orm, ory, os, pa_IN, pl_PL, pt_BR, pt_PT, ps, rhg, ro_RO, roh, ru_RU, rue, rup_MK, sah, sa_IN, si_LK, sk_SK, sl_SI, snd, so_SO, sq, sr_RS, srd, su_ID, sv_SE, sw, szl, ta_IN, ta_LK, tah, te, tg, th, tir, tlh, tl, tr_TR, tt_RU, tuk, twd, tzm, udm, ug_CN, uk, ur, uz_UZ, vec, vi, wa, xmf, yi, yor, zh_CN, zh_HK, zh-sg, zh_TW, zh.

More information in [detailed API documentation] (https://automattic.github.io/wp-cldr/class-WP_CLDR.html).

##

## Examples:
### The default locale is English
```
$cldr = new WP_CLDR();
$territories_in_english = $cldr->territories_by_locale();
```

### You can override the default locale per-call by passing in a language slug in the second parameter
```
$germany_in_arabic = $cldr->territory_name( 'DE' , 'ar' );
```

### Use a convenience parameter during instantiation to change the default locale
```
$cldr = new WP_CLDR( 'fr' );
$germany_in_french = $cldr->territory_name( 'DE' );
$us_dollar_in_french = $cldr->currency_name( 'USD' );
$canadian_french_in_french = $cldr->language_name( 'fr-ca' );
$canadian_french_in_english = $cldr->language_name( 'fr-ca' , 'en' );
$german_in_german = $cldr->language_name( 'de_DE' , 'de-DE' );
$bengali_in_japanese = $cldr->language_name( 'bn_BD' , 'ja_JP' );
$us_dollar_symbol_in_simplified_chinese = $cldr->currency_symbol( 'USD', 'zh' );
$africa_in_french = $cldr->territory_name( '002' );
```

### Switch locales after the object has been created
```
$cldr->set_locale( 'en' );
$us_dollar_in_english = $cldr->currency_name( 'USD' );
```

### Get CLDR's supplemental data
```
$telephone_code_in_france = $cldr->telephone_code( 'FR' );
```

## Links:
* http://cldr.unicode.org/
* http://cldr.unicode.org/index/cldr-spec/json
