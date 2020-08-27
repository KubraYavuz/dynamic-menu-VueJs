# dynamic-menu

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).


## React Css Notları

### React Projelerinde CSS Yazma Yöntemleri

* Inline CSS
* CSS In JS
* CSS Modules
* Sass & SCSS
* Styled Components
* Less

	Normal şartlarda React componentlerinde css kullanımı ayrı bir css dosyası oluşturup uygulama içinde çağırma şeklindedir;
 ```
.article{
  ...
}
.title{
  ...
 }
.content{
  ...
}
.image{
  ...
}
```
```
function Article({ title, content, image }) {
  return (
    <div className={styles.article}>
		<h1 className={styles.title}>{title}</h1>
		<p className={styles.content}>
			<img src={image} alt={title} className={styles.image} />
			{content}
		</p>  
    </div>
  );
}
```


#### Styled Components

   Jitsi de styled components yapısında css kullanılıyor. (package.json içerinde import edildiğini görebilirsiniz)

* Javascript içinde css yazmamızı sağlayan bir kütüphanedir.
* Ayrı bir css dosyası üzerinden style kodlarını çağırmadan browser üzerinde render lanmasını sağlar.
* Jsx üzerinde olduğu için kontrol edilmesi daha basittir ve daha hızlı bir şekilde yüklenir.
* Bu kütüphane sayesinde componentlerin state ve propslarını kullanarak dinamik css yazabiliriz.
* Alternatifleriyle yapılan karşılaştırma sonuçlarında daha başarılı olmuştur.


###### Kurulumu
```
npm install styled-components
# veya
yarn add styled-components
```

###### Örnek
```
import styled from 'styled'

const Button = styled.button`
  color: '#fff';
  background-color: purple;
  padding: 8px 16px;
  border-radius: 4px
`

const App = () => {
  return <Button />
}
```

   Yukarıda da görüldüğü gibi styled.htmlElementAdı şeklinde elementler oluşturabiliyoruz; 
   styled.h1, styled.section, styled.header gibi..

   Bu örnek sonucu, bize aşağıdaki gibi bir çıktı verir;
```
<button class=”dDMkfx”></button>
```
   Global scope sorununu çözmek için class isimlerinde unique hash kullanarak aslında bizim stillendirilmesini istediğimiz html elementini oluşturmuş olur.

   Ayrıca styled components ile oluşturulmuş bir elemanı da yeni bir componenta kalıtabiliyoruz (extend).
```
const BigButton = Button.extend`
  font-size: 32px;
  padding: 16px 24px;
`
```


##### Props İle Dinamik Styling Oluşturmak

* Styled components kütüphanesinin en güçlü özelliklerinden biridir.
* React ile uygulama geliştirirken herhangi bir veriyi props yardımıyla taşıyabiliyoruz. 
  Bu özelliği styled components ile de yaparak dinamik ve kolayca customize edilebilir componentlar oluşturabiliyoruz.
```
 const Button = styled.button`
  color: ${({ color }) => color};
  background-color: ${({ backgroundColor }) => backgroundColor};
  padding: 8px 16px;
  border-radius: 4px
`

const App = () => {
  return (
    <>
      <Button color="#fff" backgroundColor="#000">Black Button</Button>
      <Button color="#fff" backgroundColor="pink">Pink Button</Button>
    </>
  )
}
```
	Props yardımıyla Button componentinin sınırsız sayıda varyasyonunu oluşturabiliriz.


##### Global Style Oluşturmak

* Styled components ile uygulama genelinde global css blokları oluşturmak da mümkün.
```
import styled, { createGlobalStyle } from 'styled-components'

const GlobalStyle = createGlobalStyle`
  body {
    margin: 0;
    padding: 0;
    font-size: 18px;
  }

  p {
    margin-bottom: 24px;
  }
`;

const Section = styled.section`
  padding: 24px;
  border: 1px solid;
`

const App = () => {
  return (
    <>
      <GlobalStyle />
      <Section>
        Lorem Ipsum is simply dummy text of the printing and typesetting industry.
      </Section>
    </>
  )
}
```
