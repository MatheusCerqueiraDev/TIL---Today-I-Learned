
    TIL - React

    USA - Hey there!!! Good to see you here, as I described earlier, here I will share what I learned with
    you, hope to help people with this repository and make the difference for the beginners.

    PT-BR - E aii!! Que bom te ver aqui, como eu tinha dito antes, aqui eu vou compartilhar com vocês o que
    eu aprendi com você, espero poder ajudar as pessoas com esse repositorio e fazer a diferença para
    os iniciantes.

----------------------------------------------------------------------

    USA - Today (31/03/2020) I'm a junior Front end developer, I'm studying React, Typescript & Next.js at 
    Rocketseat, I already have experience with React but I lost some notes, slowly I will bring what I 
    already know

    PT-BR - Hoje (31/03/2020) Eu sou um desenvolvedor Front end junior, Eu estou estudando React, Typescript e 
    Next.js na Rockeseat, I já tenho experiencia com o React mas eu perdi algumas anotações, aos poucos
    eu vou trazendo o que eu já sei

----------------------------------------------------------------------
18/11/2021
USA REACT HOOKS RESUMED

We use React Hooks in functional components for local variables, escoped.

With React Hooks we can manipulate states, values and other react functions without create classes
Example: 

const [count, setCount] = useState(0) //here we disrupt the const so we can use immutability

return(
    <p> {count} time clicked</p>//on {count} will appear how much time the user has clicked
    <button onClick={setCount}(count + 1) //than using immutability we increase the count
    Click here</button>
)


PT-BR REACT HOOKS RESUMIDOS

Usamos REACT HOOKS dentro de components funcionais para alterar/adicionar estados locais, "escoped".

Com os Reacts Hooks podemos manipular estados, valores e outras funções sem ter que criar classes
Exemplo:

const [count, setCount] = useState(0)
//aqui desestruturamos a constante para que podemos usar a imutabilidade

return(
    <p>{count} vezes clicado</p> //indica quantos cliques ocorreram
    <button onClick={setCount(count+1)}>
    //usando o conceito de imutabilidade alteramos o valor dentro de count
    Clique aqui</button>
)

----------------------------------------------------------------------
18/11/2021
 USESTATE - REACT

 PT-BR 
 O useState é um Hook que chamamos dentro de componentes funcionais "escopados".
 Usado para alterar/adicionar valores, estados e etc de uma const. (Exemplo em REACT HOOKS RESUMIDOS)
 Chamamos o useState atráves de manipuladores de eventos.

 Podemos utilizar o useState mais de uma vez dentro do mesmo componente 
 function UsandoUseStateVariasVezes() {
  // Declara várias variáveis de state!
  const [idade, setIdade] = useState(42);
  const [fruta, setFruta] = useState('banana');
  const [todos, setTodos] = useState([{ text: 'Hooks' }]);
  // ...
}

----------------------------------------------------------------------

18/11/2021

    USEEFFECT

 USA - useEffect Function

 useEffect is a hook to observe a state & to execute code

 Where to use?

 Functional components, components from a function


 PT-BR - Função do useEffect

 useEffect é um hook para observar um estado ou rodar um codigo

 Onde usar?
 Components funcionais, componentes de uma função

----------------------------------------------------------------------
18/11/2021
 REGRAS DE USO DE HOOKS

Use hooks somente dentro de níveis superiores:
Não use hooks dentro de loops, regras condicionais(if/switch) e 
funções aninhas, funções dentro de funções.

Dessa forma, usando no nível superior da função, você garante que o seu Hook
seja chamado dentro da primeira renderização do componente.

Use Hooks somente dentro de funçõẽs React, nunca em funções Javascript

Ao invés disso 
Chame componentes React
Chame hooks personalizados

----------------------------------------------------------------------
PT-BR
CRIANDO HOOKS PERSONALIZADOS

Simulando uma ferramenta de bate papo, o hook abaixo traz se a pessoa está online ou não:

export function useFriendStatus(friendID) {
  const [isOnline, setIsOnline] = useState(null);

  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }

    ChatAPI.subscribeToFriendStatus(friendID, handleStatusChange);
    return () => {
      ChatAPI.unsubscribeFromFriendStatus(friendID, handleStatusChange);
    };
  });

  return isOnline;
}

Podemos decidir o que ele recebe como argumentos e o que ele retorna, 
Seu nome deve sempre começar com use para que você possa ver de forma fácil que as regras dos Hooks se aplicam a ele.
----------------------------------------------------------------------
PT-BR
PASSANDO INFORMAÇÕES ENTRE HOOKS

Para ilustrar isso, iremos utilizar outro componente do nosso exemplo hipotético de um chat. 
Esse é um selecionador de destinatário para mensagens do chat que mostra se o amigo selecionado está online:

const friendList = [
  { id: 1, name: 'Phoebe' },
  { id: 2, name: 'Rachel' },
  { id: 3, name: 'Ross' },
];

function ChatRecipientPicker() {
  const [recipientID, setRecipientID] = useState(1);
  const isRecipientOnline = useFriendStatus(recipientID);

  return (
    <>
      <Circle color={isRecipientOnline ? 'green' : 'red'} />
      <select
        value={recipientID}
        onChange={e => setRecipientID(Number(e.target.value))}
      >
        {friendList.map(friend => (
          <option key={friend.id} value={friend.id}>
            {friend.name}
          </option>
        ))}
      </select>
    </>
  );
}

Nós colocamos o ID do atual amigo selecionado na variável de estado (state) recipientID e atualizamos ela se o usuário escolher um amigo diferente no selecionador <select>.

Pelo fato de o Hook useState nos fornecer o último valor da variável de estado (state) recipientID, podemos passá-la para nosso Hook customizado useFriendStatus como um parâmetro

Isto nos informa se o amigo atualmente seleccionado está online. Se escolhermos um amigo diferente e atualizarmos a variável de estado recipientID, o nosso Hook useFriendStatus irá cancelar a subscrição do amigo seleccionado anteriormente, e subscrever para o status do recém-selecionado.
----------------------------------------------------------------------
PT-BR
PROPS 

function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

<Welcome name="Sara" />;

Um elemento representando um componente definido pelo usuário,
ele passa atributos JSX e componentes filhos para esse componente como um único objeto.
Nós chamamos esse objeto de “props”.

1. Nós chamamos o elemento <Welcome name="Sara" />.
2.React chama o componente Welcome com {name: 'Sara'} como props.
3.Nosso componente Welcome retorna um elemento <h1>Hello, Sara</h1> como resultado.
4.React DOM atualiza eficientemente o DOM para corresponder <h1>Hello, Sara</h1>.

----------------------------------------------------------------------
PT-BR
Convertendo uma Função para uma Classe

1.Criar uma classe ES6 estendendo React.component.
2.Adicionar um único método vazio chamado render().
3.Crie a função dentro do método render().
4.Substitua props por this.props no corpo de render().
Exemplo:
class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.props.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

O método render será chamado toda vez que uma atualização acontecer, mas enquanto renderizarmos <Clock> no mesmo nó DOM, apenas uma única instância da classe Clock será usada. Isso nos permite usar recursos adicionais, como o estado local e os métodos de ciclo de vida.

----------------------------------------------------------------------
PT-BR
Adicionando Estado Local a uma Classe

Vamos mover a date da props para o state em três passos:

1.Substitua this.props.date por this.state.date no método render():
class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

2.Adicione um construtor na classe que atribui a data inicial no this.state:
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

3.Note como nós passamos props para o construtor:

  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }
Componentes de classes devem sempre chamar o construtor com props.

Remova a props date do elemento <Clock />:
ReactDOM.render(
  <Clock />,
  document.getElementById('root')
);

O resultado:
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

ReactDOM.render(
  <Clock />,
  document.getElementById('root')
);
----------------------------------------------------------------------
PT-BR
Adicionando Métodos de Ciclo de Vida a Classe

1.Quando <Clock /> é passado para ReactDOM.render(), o React chama o construtor do componente Clock. Como Clock precisa exibir a hora atual, ele inicializa this.state com um objeto incluindo a hora atual. Mais tarde, atualizaremos este state.
2.React chama então o método render() do componente Clock. É assim que o React aprende o que deve ser exibido na tela. React em seguida, atualiza o DOM para coincidir com a saída de renderização do Clock.
3.Quando a saída do Clock é inserida no DOM, o React chama o método do ciclo de vida componentDidMount(). Dentro dele, o componente Clock pede ao navegador para configurar um temporizador para chamar o método tick() do componente uma vez por segundo.
4.A cada segundo o navegador chama o método tick(). Dentro dele, o componente Clock agenda uma atualização de UI chamando setState() com um objeto contendo a hora atual. Graças à chamada setState(), o método render() será diferente e, portanto, a saída de renderização incluirá a hora atualizada. React atualiza o DOM de acordo.
5.Se o componente Clock for removido do DOM, o React chama o método do ciclo de vida componentWillUnmount() para que o temporizador seja interrompido