## Kendim Deneyimlediğim Notlardır
```
***********************************************************************************************************************
- Bu ikisi bir biriyle bağlı [flexDirection, justifyContent], kullanacaksak ikisini birden kullanmak gerek.
	
	- flexDirection:
		- row				: nesleri yatay hizalar
		- row-reverse		: nesleri yatay hizalar (tersten)
		- column			: nesleri diker hizalar
		- column-reverse	: nesleri diker hizalar (tersten)
		
	- justifyContent (Dikey):
		- flex-start		: sol üstten hizalama yapar
		- flex-end			: en alttan hizalama yapar
		- center			: ortalı bir şekilde hizalama yapar
		- space-between		: en üst, en alt ve en orta olacak şekilde hizalama yapar
		- space-around		: en üstten ve en alttan biraz boşluk bırakacak şekilde hizalama yapar
		- space-evenly		: en üstten ve en alttan daha fazla boşluk bırakacak şekilde hizalama yapar
		
	- flexWrap:
		- nowrap:			: nesneleri iç içe veya alt alta taşmasını sağlar
							:
							:	[1][2][3][4][5][6][7][8][9]
							:	[2]
							:	[3]
							:	[4]
							:	[5]
							:	[6]
							:	[7]
							:	[8]
							:	[9]
							:
		- warp:				: nesnelerin taştığı durumda alt alta veya yan yana sıralama yapar
							:
							:	[1] [2] [3]
							:	[4] [5] [6]
							:	[7] [8] [9]
							:
		- wrap-reverse		: nesneleri taşmadan dolduracak şekilde tersten hizalar
							:
							:	[9] [8] [7]
							:	[6] [5] [4]
							:	[3] [2] [1]
							:

	- alignSelf (?):
		-	*
		-	* Bir içeriği soldan, sağdan ve ortadan hizalar.
		-	* Bu hizalamayı yaparken alignItems işlevini yok sayar.
		-	* Ayrıca tüm alanı kaplamaz alanın iç doluluğu kadarını kapsar
		-	*
		-	* Kaplama Örneği:
		-	*	................
		-	*	 Merhaba Dünya
		-	*	................
		-	*
		-	*
		-	* Yok Sayma Örneği:
		-	*	Metin 1
		-	*		Metin 2
		-	*	Metin 3
		-	*
		-	*
		-
		- baseline			: en soldan hizalama yapar (varsayılan flex-start)
		- center			: en ortadan hizalama yapar
		- flex-end			: en sağdan hizalaam yapar
		- flex-start		: en soldan hizalama yapar
		- stretch			: en soldan hizalama yapar

	- alignItems (Yatay):
		-	*
		-	* Bir içeriği soldan, sağdan ve ortadan hizalar.
		-	* Ayrıca tüm alanın iç doluluğu kadarını kapsar
		-	*
		-	* Kaplama Örneği:
		-	*	X....................................X
		-	*				Merhaba Dünya
		-	*	X....................................X
		-	*
		-	*
		-	*	X....................................X
		-	*		Merhaba Dünya
		-	*	X....................................X
		-
		- baseline			: en soldan hizalama yapar (varsayılan flex-start)
		- center			: en ortadan hizalama yapar
		- flex-end			: en sağdan hizalaam yapar
		- flex-start		: en soldan hizalama yapar
		- stretch			: en soldan hizalama yapar
		
		
	- alignContent:
		- flex-start		: sol üstten hizalama yapar
		- flex-end			: en alttan hizalama yapar
		- center			: ortalı bir şekilde hizalama yapar
		- space-between		: en üst, en alt ve en orta olacak şekilde hizalama yapar
		- space-around		: en üstten ve en alttan biraz boşluk bırakacak şekilde hizalama yapar
		- space-evenly		: en üstten ve en alttan daha fazla boşluk bırakacak şekilde hizalama yapar

	- direction:
		- ltr				: nesneyi sola dayar
		- rtl				: nesneyi sağa dayar
		
	- gap					: flexWrap, flexDirection ile kullanılan dikey ve yatay arası mesafe boşluklarını belirler
	- rowGap				: flexWrap, flexDirection ile kullanılan dikey boşluk mesafesini belirler
	- columnGap				: flexWrap, flexDirection ile kullanılan yatay boşluk mesafesini belirler
	
	- width					: genişlik ayarlar
	- height				: yükseklik ayarlar
	
	- overflow:
		- hidden			: flexWrap da kullanılan taşmayı gizler
		- scroll			: kaydırılabilir liste olur
		- visible			: taşmayı gösterir
	
	- position:
		- absolute			: konumu istediğin gibi ayarlar (top, left, right, bottom)
		- static / relative	: konum normal ayarlama şekline döner
```
