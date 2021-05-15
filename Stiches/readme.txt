STICHES

Stiches veio para tentar substituir o styled components:

Diferenças de API
Importando a styledfunção
Em componentes estilizados, a styledfunção é uma importação padrão.

Em Stitches, a styledfunção é uma importação nomeada.

 styled-components
import styled from 'styled-components';

 Stitches
import { styled } from '@stitches/react';


Sintaxe de objeto apenas
Em componentes estilizados, você pode escrever CSS em strings de modelo ou em uma sintaxe de objeto.

Em Stitches, você escreve CSS usando a sintaxe de estilo de objeto . Os motivos para isso são:
desempenho, tamanho do pacote e experiência do desenvolvedor
 (verificações de tipo e sugestões de preenchimento automático para propriedades e valores).


 styled-components
const Button = styled.button`
  color: red;
  font-size: 14px;
  ':hover' {
    color: black;
    font-size: 14px;
  }
`;

 Stitches
const Button = styled('button', {
  color: 'red',
  fontSize: '14px';
  '&:hover': {
    color: 'black',
    fontSize: '14px';
  },
});

Seletores de encadeamento
Em componentes estilizados, pseudo classes e pseudo seletores são automaticamente encadeados ao seletor
com escopo. No entanto, outros seletores, como seletores de classe ou id, exigem o &sinal,
caso contrário, eles são considerados descendentes.

Em pontos, todos os seletores encadeados exigem o &sinal.

const Button = styled.button`
  // chained
  :hover {
  }

  // chained
  ::before {
  }

  // descendant
  .class {
  }
`;

// Stitches
const Button = styled('button', {
  // all chained
  '&:hover': {},
  '&::before': {},
  '&.class': {},
});

Prop Interpolation vs Variants
Em componentes com estilo, você pode interpolar os adereços do componente para definir estilos
condicionalmente.

Em Stitches, apresentamos o conceito de variantes . Você pode aplicar variantes condicionalmente
no nível de consumo, inclusive em diferentes pontos de interrupção.

 styled-components
const Button = styled.button`
  ${(props) =>
    props.color === 'violet' &&
    `
    background-color: 'blueviolet'
  `}

  ${(props) =>
    props.color === 'gray' &&
    `
    background-color: 'gainsboro'
  `}
`;

 Stitches
const Button = styled('button', {
  variants: {
    color: {
      violet: { backgroundColor: 'blueviolet' },
      gray: { backgroundColor: 'gainsboro' },
    },
  },
});

() => <Button color="violet">Button</Button>;

okens e temas
Em componentes estilizados, você pode adicionar um tema por meio do <ThemeProvider/>.
O tema é injetado em todos os componentes e você pode acessá-lo por meio de interpolação de prop.

Em Stitches, você pode definir tokens no arquivo de configuração e consumir e acessar
 diretamente no objeto de estilo.

 // styled-components
import { ThemeProvider } from 'styled-components';

() => (
  <ThemeProvider
    theme={{
      colors: {
        red500: 'tomato',
      },
      space: {
        1: '5px',
        2: '10px',
      },
    }}
  >
    <App />
  </ThemeProvider>
);

const Button = styled.button`
  color: ${(props) => props.theme.colors.red500};
  margin: ${(props) => `${props.theme.space[1]} ${props.theme.space[2]}`};
`;

// Stitches
const { styled } = createCss({
  theme: {
    colors: {
      red500: 'tomato',
    },
    space: {
      1: '5px',
      2: '10px',
    },
  },
});

const Button = styled('button', {
  color: '$red500',
  margin: '$1 $2',
});

Estilos Responsivos
Em componentes estilizados, você pode adicionar at-rules diretamente no CSS.

Em Stitches, você pode fazer o mesmo. Mas você também pode definir pontos de
interrupção no mediaobjeto e acessá- los diretamente no objeto de estilo.

// styled-components
const Box = styled.div`
  padding: 12px;

  @media (min-width: 480px) {
    padding: 24px;
  }
`;

// Stitches
const { styled } = createCss({
  media: {
    '@bp1': '(min-width: 480px)',
  },
});

const Box = styled('div', {
  padding: '12px',

  '@bp1': {
    padding: '24px',
  },
});


Estilos Globais
Em componentes estilizados, você pode adicionar estilos globais com a createGlobalStyleAPI.

Em Stitches, você pode usar a globalAPI.

// styled-components
import { createGlobalStyle } from 'styled-components';

const GlobalStyles = createGlobalStyle`
  body {
    margin: 0
  }
`;

// Stitches
import { global } from '@stitches/react';

global({
  body: {
    margin: '0',
  },
});


Animações
Em componentes estilizados, você pode importar a keyframesfunção diretamente de styled-components.

Em pontos, você pode usar a keyframesfunção.

// styled-components
import { keyframes } from 'styled-components';

const fadeIn = keyframes`
  0% { opacity: 0 }
  100% { opacity: 1 }
`;

const Box = styled.div`
  animation-name: ${fadeIn};
`;

// Stitches
import { keyframes } from '@stitches/react';

const fadeIn = keyframes({
  '0%': { opacity: '0' },
  '100%': { opacity: '1' },
});

const Box = styled('div', {
  animationName: fadeIn,
});
Renderização do lado do servidor
Em componentes estilizados, você cria ServerStyleSheetou StyleSheetManagerdepende de suas necessidades.

Em Stitches, você usa a getCssStringfunção. Saiba mais sobre renderização do lado do servidor .
Muitas bibliotecas de IU documentam que as variantes responsivas não funcionam com a renderização do lado do servidor. Stitches suporta renderização do lado do servidor em vários navegadores, mesmo para estilos responsivos e variantes.

Por trás das cenas
Stitches é uma biblioteca de estilo leve e de alto desempenho com foco na arquitetura de componentes
e na experiência do desenvolvedor.

Desempenho
Stitches evita interpolações de prop desnecessárias em tempo de execução, tornando-o mais eficiente
do que outras bibliotecas de estilo.

Tanto as bibliotecas @stitches/corequanto as @stitches/reactcombinadas pesam aproximadamente 4,7 kb gzip.

Experiência do desenvolvedor
Stitches é baseado em TypeScript. Por padrão, tudo o que você faz em pontos será verificado por tipo.
Como usuário, você receberá sugestões de preenchimento automático para Propriedades CSS, uso de token
em valores, pontos de interrupção e atributos de elementos relacionados. As variantes também são
digitadas automaticamente.