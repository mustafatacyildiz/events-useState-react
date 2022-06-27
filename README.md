// * =======================================================
// *                     EVENTS
// * =======================================================

ReactJS, Tarayicilar arasi uyumluluk ve performans artisi gibi sebeplerden oturu Sentetik Event olarak adilandirilan Olaylari kullanir. Sentetik Event, aslinda tarayicinin dogal event'larinin bir sarmalayici (Wrapper) arabirimle ortulmesi ile olusur. Bu sayede, React ortaminda kullanilan event'larin bilindik tarayicilarda sorunsuz calismasini saglanir. Ayrinti icin : https://reactjs.org/docs/events.html



 Eger bir event fonksiyonunun paremetresi olmasi gerkiyorsa  bu fonksiyon bir arrow fonks. tarafindan  cagrilmalidir. Aksi  takdirde event fonksiyonu event gerceklesmeden cagirilir.

 const Events = () => {
  const handleClick = () => {
    alert('Btn Clicked');
  };
  const handleClear = (text) =>{
    alert(text)
  };
  return (
    <div className="container text-center mt-4">
      <button onClick={handleClick} className="btn btn-warning">
        Click
      </button>
      <button onClick={()=> handleClear("Clear Btn pressed")} className="btn btn-dark">Clear</button> #Arrow function ile kullanımı
    </div>
  );
};

info console'da guncellendigini ancak DOM'da guncellenmedigini gorduk. Bunun sebebi REACT'in aksi belirtilmedigi surece elementleri static olarak kabul etmesinden kaynaklanir.

React bunu DOM islemlerini minimize etmek icin yapmaktadir. REACT'a hangi elementleri interaktif oldugu belirtilmelidir.
React'a elementlerin interaktif oldugunu belirtmek icin state'ler kullanilir.
State, elementlerin degisiklik durumlarini tutan nesnelerdir.
ReactJs'de state'leri kullanmak icin  2 ayri Component yapisi bulunmaktadir.
1. Statefull Classes (Class Components).
2. Hooks (Functional Components).

Biz su ana kadar uygulamalarimizda Fonksiyonel Component'leri kullandik.
Yaygin kullanim Fonksiyonel Component'lerdir.


===================== CLASS COMPONENTS AND STATE============================
React'da Class-Component'ler ES6 class yapisina dayanmaktadir. 
Cok fazla boilerplate kod icermektedir. 
Ancak Class-Component'ler React'da state'leri barindiran ilk component yapisidir.
State, aslinda bir component hakkinda bilgi tutan bir React nesnesidir. 
Bir componentin state'i zaman icerisinde degisebilir. State her degistiginde React bu componenti yeninden render eder. 
Bir state'e baslangıc degeri constructor metodu icersinde this.state ile atanabilir. 
Constructor'in disinda state, setState() metodu ile degistilebilir.
 ===============================================================================

 There are 2 important points we need to pay attention to when using state:
● State shouldn’t be modified directly – the setState( ) should be used.
● State affects the performance of your app, and therefore it shouldn’t be used unnecessarily.

What are the differences between props and state?
➤ Finally, let’s recap and see the main differences between props and state:
● Components receive data from outside with props, whereas they can create and manage their own data with state
● Props are used to pass data, whereas state is for managing data
● Data from props is read-only, and cannot be modified by a component that is receiving it from outside
● State data can be modified by its own component, but is private (cannot be accessed from outside)
● Props can only be passed from parent component to child (unidirectional flow)
● Modifying state should happen with the setState ( ) method



Yazmis oldugumuz metotlar default olarak classa baglanmaz.Ancak, React built-in fonksiyonlari baglidir.
Bunun icin metotlarimizi ya constructor icerisinde baglamaliyiz yada otomatik baglamayi saglayan arrow fonksiyonlarini kullanmaliyiz.


//* ========================== HOOKS ====================================
Hook'lar fonksiyonel component'ler icerisinde state'leri kullanmamiza
olanak saglayan ozel fonksiyonlardir.
React 16.8 versiyonu ile gelmistir ve geldikten sonra Class-componentler'in kullanimi cok azaltmistir.

React'ta useState(), useEffect(), useContext() gibi bir cok built-in
Hook bulunmaktadir. Ayrica custom hook tanimlamak da mumkundur.

//* Hook Kullanim Kurallari:
1. İlk olarak import edilmedlir. import { useState } from "react";
2. Hook'lar ust seviyede kullanilmalidir. Yani Hook'lar bir
dongunun, kosul cumleciginin ve icice fonksiyonlarin icerisinde kullanilmamalidir.
3. Hook'lar sadece React Fonksiyonel componentleri icerisinde cagrilmalidir.
Normal Javascript fonksiyonlari icerisinde cagrilmamalidir
(Custom hook'lar icerisinde bir hook cagrilabilir)
 https://reactjs.org/docs/hooks-rules.html
//* =====================================================================
                        =====useState===

useState
Bir state in degisken,
ve obje ile kutlanilabilmesine olanak saglar
useState hook'u 2 deger dondurur.

1. si state degiskenidir.
2. si ise state"i degistirmeye izin veren bir setter metodudur.
useState parametre olarak state'in ilk degerini alir.