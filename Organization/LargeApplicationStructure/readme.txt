
Como organizar pastas de um projeto grande e escalavel.

Antes de tudo, gostaria de deixa claro que não existe a maneira certa de se estruturar/organizar 
um projeto, vai de cada qual.

A referência que vou passar aqui você acha nesse link:
    https://www.robinwieruch.de/react-folder-structure/

Quando você está trabalhando em um pequeno projeto ou em um time de desenvolvimento multi-funcional
é normal você mover os arquivos até que estejam "visualmente agradavel".

Mas quando partimos para uma grande empresa e participamos de um projeto onde temos diversos times,
e todos são multi-funcionais, temos que adotar um padrão claro, objetivo e intuitivo para a comunicação indireta.


Aqui vão algumas dicas para organizar grandes projetos:

1° Já é costume que o o App.js receba todos componentes que constituem a aplicação, 
a nomeação de componentes com nomes claros se faz necéssario para que todos entendam o que aquele componente é.

import React from 'react';

const App = () => {
  const title = 'React';

  return (
    <div>
      <h1>Hello {title}</h1>
    </div>
  );
}

export default App;

A segunda dica é a desestruturação de componentes, exemplo:

Componente Header[
    componente Logo{

    },
    componente NavBar{

    },
    componente Profile{

    },
]

Para que fique claro a explicação acima... Basicamente podemos criar pequenos componentes para construirmos um componente grande.


3° Separação de pastas de componentes.

Para maior organização e facilidade de leitura estruturamos nossas pastas components:

-Pasta components

--Header
-index
---Logo
----index
---NavBar
----index

--Sidebar <- Nome do componente/Componente Maior
-index <- Seu index
---SidebarLink <- Componente menor
----index <- Seu index
---SidebarItens <- Componente menor
----index <- Seu index

Resumo final:

Estruturando suas pastas desse jeito você ganha grandes beneficíos com essas pequenas tarefas,
com essa estruturação você pode reutilizar componentes alé de deixar mais fácil a localização 
dos mesmos.