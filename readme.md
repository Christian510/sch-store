In case updates to theme kit cause issues you can role back updates ith th following command;

 'theme update --version=v1.2.0'

 07/21/2021: directory: locales; products.sold_out, changed the value to "Coming Soon"

 schema template

 "settings": [
     {
     "type": "checkbox",
     "id": "show_product_announcement_banner"
     "label": {
         "en": "Show Announcement Banner"
     },
     "default": false
     },
      "type": "checkbox",
      "id": "message",
      "label": {
        "cs": "Zobrazit oznámení",
        "da": "Vis meddelelse",
        "de": "Ankündigung anzeigen",
        "en": "Show announcement",
        "es": "Mostrar anuncio",
        "fi": "Näytä ilmoitus",
        "fr": "Afficher l'annonce",
        "it": "Mostra annuncio",
        "ja": "告知を表示する",
        "ko": "공지 표시",
        "nb": "Vis kunngjøring",
        "nl": "Aankondiging weergeven",
        "pl": "Pokaż ogłoszenie",
        "pt-BR": "Exibir comunicado",
        "pt-PT": "Mostrar comunicado",
        "sv": "Visa tillkännagivande",
        "th": "แสดงประกาศ",
        "tr": "Duyuruyu göster",
        "vi": "Hiển thị thông báo",
        "zh-CN": "显示公告",
        "zh-TW": "顯示公告"
      },
      "default": false
    },
    {
      "type": "text",
      "id": "message_text",
      "label": {
        "cs": "Text",
        "da": "Tekst",
        "de": "Text",
        "en": "Text",
        "es": "Texto",
        "fi": "Teksti",
        "fr": "Texte",
        "it": "Testo",
        "ja": "テキスト",
        "ko": "텍스트",
        "nb": "Tekst",
        "nl": "Tekst",
        "pl": "Tekst",
        "pt-BR": "Texto",
        "pt-PT": "Texto",
        "sv": "Text",
        "th": "ข้อความ",
        "tr": "Metin",
        "vi": "Văn bản",
        "zh-CN": "文本",
        "zh-TW": "文字"
      },
      "default": {
        "cs": "Tady můžete zadat oznámení",
        "da": "Meddel noget her",
        "de": "Hier etwas ankündigen",
        "en": "Announce something here",
        "es": "Anuncia algo aquí",
        "fi": "Ilmoita jotakin tässä",
        "fr": "Annoncez quelque chose ici",
        "it": "Annuncia qualcosa qui",
        "ja": "ここで告知してください",
        "ko": "여기에 공지하십시오",
        "nb": "Kunngjør noe her",
        "nl": "Kondig hier iets aan",
        "pl": "Ogłoś coś tutaj",
        "pt-BR": "Anuncie algo aqui",
        "pt-PT": "Anunciar algo aqui",
        "sv": "Meddela något här",
        "th": "ประกาศข้อความที่นี่",
        "tr": "Buraya bir duyuru ekleyin",
        "vi": "Thông báo điều gì đó tại đây",
        "zh-CN": "在此处进行公告",
        "zh-TW": "在此公告資訊"
      }
    },
        {
      "type": "url",
      "id": "message_link",
      "label": {
        "cs": "Odkaz",
        "da": "Link",
        "de": "Link",
        "en": "Link",
        "es": "Enlace",
        "fi": "Linkki",
        "fr": "Lien",
        "it": "Link",
        "ja": "リンク",
        "ko": "링크",
        "nb": "Kobling",
        "nl": "Link",
        "pl": "Link",
        "pt-BR": "Link",
        "pt-PT": "Ligação",
        "sv": "Länk",
        "th": "ลิงก์",
        "tr": "Bağlantı",
        "vi": "Liên kết",
        "zh-CN": "链接",
        "zh-TW": "連結"
      },
      "info": {
        "cs": "Volitelné",
        "da": "Valgfri",
        "de": "Optional",
        "en": "Optional",
        "es": "Opcional",
        "fi": "Valinnainen",
        "fr": "Facultatif",
        "it": "Facoltativo",
        "ja": "オプション",
        "ko": "선택 사항",
        "nb": "Valgfritt",
        "nl": "Optioneel",
        "pl": "Opcjonalnie",
        "pt-BR": "Opcional",
        "pt-PT": "Opcional",
        "sv": "Valfritt",
        "th": "ไม่จำเป็น",
        "tr": "İsteğe bağlı",
        "vi": "Không bắt buộc",
        "zh-CN": "可选",
        "zh-TW": "(選填)"
      }
    },
        {
      "type": "color",
      "id": "color_bg",
      "label": {
        "cs": "Panel",
        "da": "Bjælke",
        "de": "Zeile",
        "en": "Bar",
        "es": "Barra",
        "fi": "Palkki",
        "fr": "Barre",
        "it": "Barra",
        "ja": "バー",
        "ko": "바",
        "nb": "Felt",
        "nl": "Balk",
        "pl": "Pasek",
        "pt-BR": "Barra",
        "pt-PT": "Barra",
        "sv": "Fält",
        "th": "แถบ",
        "tr": "Çubuk",
        "vi": "Thanh",
        "zh-CN": "栏",
        "zh-TW": "橫條"
      },
      "default": "#3a3a3a"
    },
    {
      "type": "color",
      "id": "color_text",
      "label": {
        "cs": "Text",
        "da": "Tekst",
        "de": "Text",
        "en": "Text",
        "es": "Texto",
        "fi": "Teksti",
        "fr": "Texte",
        "it": "Testo",
        "ja": "テキスト",
        "ko": "텍스트",
        "nb": "Tekst",
        "nl": "Tekst",
        "pl": "Tekst",
        "pt-BR": "Texto",
        "pt-PT": "Texto",
        "sv": "Text",
        "th": "ข้อความ",
        "tr": "Metin",
        "vi": "Văn bản",
        "zh-CN": "文本",
        "zh-TW": "文字"
      },
      "default": "#ffffff"
    }
  ]
}
 ]