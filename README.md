# Lab10Web (PRAKTIKUM 10 : PHP OOP)

## Langkah 1 
### Buat file di `C:\xampp\htdocs` seperti berikut `lab10_php_oop`
<img src=Praktikum10/0.png>
- Note : Pastikan sudah membuka XAMPP dan start MySQL dan Apache nya

## Langkah 2
### Membuat `mobil.php`
```
<?php
class Mobil
{
    private $warna;
    private $merk;
    private $harga;
    public function __construct()
    {
        $this->warna = "Biru";
        $this->merk = "BMW";
        $this->harga = "10000000";
    }
    public function gantiWarna ($warnaBaru)
    {
        $this->warna = $warnaBaru;
    }
    public function tampilWarna ()
    {
        echo "Warna mobilnya : " . $this->warna;
    }
}
// membuat objek mobil
$a = new Mobil();
$b = new Mobil();
// memanggil objek
echo "<b>Mobil pertama</b><br>";
$a->tampilWarna();
echo "<br>Mobil pertama ganti warna<br>";
$a->gantiWarna("Merah");
$a->tampilWarna();
// memanggil objek
echo "<br><b>Mobil kedua</b><br>";
$b->gantiWarna("Hijau");
$b->tampilWarna();
?>
```
## Hasilnya 
<img src=Praktikum10/2.png>

## Langkah 3
### Membuat `form.php`
```
<?php
class Form
{
	private $fields = array();
	private $action;
	private $submit = "Submit Form";
	private $jumField = 0;
	
	public function __construct($action, $submit)
	{
		$this->action = $action;
		$this->submit = $submit;
	}

	public function displayForm()
	{
		echo "<form action='".$this->action."' method='POST'>";
		echo '<table width="25%" border="0">';
		for ($j=0; $j<count($this->fields); $j++) 
		{
			echo "<tr><td align='left'>".$this->fields[$j]['label']."</td>";
			echo "<td><input type='text'name='".$this->fields[$j]['name']."'></td></tr>";
		}
		echo "<tr><td colspan='2'>";
		echo "<input type='submit' value='".$this->submit."'></td></tr>";
		echo "</table>";
	}

	public function addField($name, $label)
	{
		$this->fields [$this->jumField]['name'] = $name;
		$this->fields [$this->jumField]['label'] = $label;
		$this->jumField ++;
	}
}
?>
```

## Langkah 4
### Membuat `form_input.php`
```
<?php
include "form.php";

echo "<html><head><title>Mahasiswa</title></head><body>";
$form = new Form("","Input Form");
$form->addField("txtnim", "Nim");
$form->addField("txtnama", "Nama");
$form->addField("txtalamat", "Alamat");
echo "<h3>Silahkan isi form berikut ini :</h3>";
$form->displayForm();
echo "</body></html>";

?>
```

## Hasilnya
<img src=Praktikum10/6.png>

- Note : 
```
form_input.php akan otomatis tersinkron dengan form.php 
sehingga saat form_input.php dipanggil, 
form.php juga akan terpanggil, oleh karena itu saat memanggil form.php 
tidak terjadi apa apa
```

```
Nama  : Ario Fajar
NIM   : 311910610
Kelas : TI.19.A2
```
