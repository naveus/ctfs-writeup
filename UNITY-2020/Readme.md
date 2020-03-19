# UNITY-2020 Writeup
<p align="center">
<img width="460" height="300" src="https://i.ibb.co/CbJqWst/KKN.png"> <br>
KKN Back To Isekai - STT Bandung 
</p>

### Challenges

<table align="center">
</tr>
	<tr>
		<td>Category</td>
		<td>Challenges</td>
		<td>Solves</td>
		<td>Points</td>
	</tr>
	<tr>
		<td rowspan=2>Forensics</td>
    	<td> P</td>
	    <td> 38</td>
	    <td>137</td>
	</tr>
	<tr>
		<td>Neet Diary</td>
		<td>0</td>
		<td>500</td>
	</tr>
	<tr>
		<td>Web</td>
		<td> Stromeo </td>
		<td> 27 </td>
		<td> 137 </td>
	</tr>
	<tr>
		<td>Crypto</td>
		<td>Klepto</td>
		<td>15</td>
		<td>137</td>
	</tr>

</table>

#### Forensics
- P <br>
	Diberikan sebuah *attachment file packet data*. Pertama, kami melakukan information gathering terhadap file packet data tersebut menggunakan bantuan [tshark](https://github.com/hasanbulat/tshark). 
	
	<img src="http://imgur.com/fS4GPnzl.png" />

	Dapat diketahui, *packet data* tersebut memuat 843 Frames dan 84340 Bytes. Setelah itu, kami melakukan analisa ip mana saja yang melakukan *conversation* 
	
	<img src="http://imgur.com/UVEtzyfl.png" />

	Seperti yang bisa kita lihat, ada 3 ip yang menjadi *source* dan 1 ip yang menjadi *server* saat melakukan *conversation*. 

	Awalnya, kami menggali informasi pada Ip **13.78.65.168** , namun tidak ada yang mencurigakan walaupun ip tersebut memuat lebih banyak bytes daripada ip yang lainnya. Selanjutnya, kami melakukan enumerasi informasi kembali pada ip selanjutnya, yaitu **182.1.70.81**
	
	<img src="http://imgur.com/iLoeTr7l.png" />

	Seperti yang bisa kita lihat, pada *offset* **0030** terdapat 1 *character* yang berubah ubah. Hal tersebut membuat kami curiga bahwa character tersebut merupakan *statisfiable data* yang menggunakan *encoding base64*.

	Maka dari itu, kami melakukan *filtering* data lebih spesifik untuk mendapatkan *character encoding* tersebut
	
	<img src="http://imgur.com/H6jINnYl.png" />
	
	**UNITY2020{PING_PONG_Seikai_Desu!!!!:D}**
