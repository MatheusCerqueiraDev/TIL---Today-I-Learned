

MATERIAL-UI

Biblioteca de design system, assim como Chakra-ui, essa biblioteca vem com componetnes pre-prontos
podendo você estilizar shapes e cores.

Para o uso desses componentes pre-prontos basta uma importação dentro do componente sendo criado.

----------------------------------------------------------------------

Material-ui com React

Para instalarmos o React digitamos no terminal:

yarn create react-app *nome do seu programa*

Após a criação adicionamos o MUI

yarn add @material-ui/core.

----------------------

Importações

Na documentação mostra como podemos fazer a importação de um unico componente por sua lib:

import Button from '@material-ui/core/Button' 

Mas podemos usar uma única importação para quase todos componentes:

import Button from '@material-ui/core/Button' 

----------------------

Utilização

Assim como um componente chamamos o componente do MUI usamos a semantica seguinte:

import Button from '@material-ui/core/Button'

function App() {
  return (
      <Button>
        Hello World
      </Button> <- Componente MUI     !!!!
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
      </header>
    </div>
  );
}

----------------------

Estilização

Como estamos lidando com um design system a estilização de seus componentes é feita in-line.

Passamos o "modelo" do botão com a propiedade (variant)

import Button from '@material-ui/core/Button'

function App() {
  return (
    <Button variant="text">Text</Button> <- Botão sem preenchimento
    <Button variant="contained">Contained</Button>
    <Button variant="outlined">Outlined</Button> 
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
      </header>
    </div>
  );
}


Para darmos cor aos nossos componentes passamos a prop (color)

<Button color="primary">Contained</Button>


Como todo botão, os botões do MUI também podem receber (href) para linkarmos

<Button href="*link*">Contained</Button>

Esses componentes do MUI também podem receber eventos Javascript assim como um HTML button

<Button onClick={() => alert("hello World")}>Contained</Button>

Podemos também passa a propiedade para desabilitar o button

<Button disabled>Contained</Button>

Alteramos o tamanho do componente com a prop (size)

<Button size="large">Contained</Button>
<Button size="medium">Contained</Button>
<Button size="small>Contained</Button>

Para sobre escrever estilizações padrões do Material-Ui usamos a props (styles)
Exemplo: Caso a cor padrão de um botão venha azul podemos sobre escreve-lo assim:

<Button styles={color="primary.red"}>Contained</Button>

----------------------------------------------------------------------

Uso de Icones com MUI

Antes de tudo é necéssario instalarmos a biblioteca de icons do MUI

yarn add @material-ui/icons

*Caso seu servidos (localhost) estiver rodando é necéssario reiniciar o mesmo

----------------------

Importações dos Icones

Para usarmos os icones baixados, fazemos a importação de um componente, ou seja, sem chaves

import SaveIcon from '@material-ui/icons/SaveIcon'
import { Save, ThreeDRotation } from "@material-ui/icons";

----------------------

Uso dos Icones

Como dito, esse icones são importados como componentes e o uso também será como componente

Dentro de um Button passamos o icone como prop, mas ainda sim o icone é referenciado com um componente

Podemos adicionar um Icone no inicio do button com:

<Button startIcon={<Save/>}>Contained</Button>

E ao final do Button com:

<Button endIcon={<Save/>}>Contained</Button>

----------------------

Button Group 

O button group é um componente e funciona pra mesclar os botões dentro dele, dando um visual mais atrativo.

Ele transforma dois botões em um único botão e no seu início e fim com bordar arredondas.

----------------------

Importação ButtonGroup 

O Button group vem por padrão dentro no @material-ui/core
Para sua importação utilizamos a seguinte linha:

import ButtonGroup from '@material-ui/core/ButtonGroup'

----------------------

Exemplo:

import ButtonGroup from '@material-ui/core/ButtonGroup'

export function ButtonGroup() {
    return(
        <ButtonGroup>
            <Button>
              First Button  
            </Button>
            <Button>
              Second Button  
            </Button>
        </ButtonGroup>
    )
}

Isso deve retornar dois botões mesclados.

----------------------

Estilos do Button Groups

Podemos dar estilizações todos butões dentro do Button Group inserindo propiedades ao componente:

import ButtonGroup from '@material-ui/core/ButtonGroup'

export function ButtonGroup() {
    return(
        <ButtonGroup variant="contained">
            <Button>
              First Button  
            </Button>
            <Button>
              Second Button  
            </Button>
        </ButtonGroup>
    )
}

----------------------------------------------------------------------

CheckBox

Checkbox são utilizados dentro de formularios

O componente checkbox no MUI se faz necéssario o uso da lógica de desestruturação
 e é viável cria-lo em um componente separado.

Exemplo:

export function ExemploCheckBox(){
  const {checked, setChecked} = React.useState(true)

  return(
    <Checkbox/>
  )
}

----------------------

Propiedades obrigatorias do checkbox

O componente CheckBox do MUI recebe por padrão propiedades para que funcione, 
caso contrário ele não funcionará, as propiedades:

export function ExemploCheckBox(){
  const [checked, setChecked] = React.useState(true)

  return(
    <Checkbox
    checked={checked}     <- verificação se está true or false
    onChange={(e) => {setCheked(e.target.value.checked)}}
    />
  )
}

----------------------

Propiedades

Como os outros componentes o check box recebe outras propiedades de estilização:

export function ExemploCheckBox(){
  const [checked, setChecked] = React.useState(true)

  return(
    <Checkbox
    color="primary"
    
    />
  )
}