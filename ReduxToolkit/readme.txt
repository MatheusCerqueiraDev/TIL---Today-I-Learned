

Redux ToolKit

Proposito

O RTK foi criado em cima da lógica da ferramenta Redux.

Ele veio para facilitar a criação de chamadas em Redux.
Reduzir a quantidade de pacotes a serem intalados juntos.
E para reduzir o uso de BoilerPlates.

O Redux Toolkit também inclui um poderoso recurso de busca e armazenamento de dados que chamamos de RTXQuery.

Instalação

# Redux + Plain JS template
npx create-react-app my-app --template redux

# Redux + TypeScript template
npx create-react-app my-app --template redux-typescript

Em apps já existentes

# Yarn
yarn add @reduxjs/toolkit

Incluso na instalação

#configureStore: envolve o createStore para fornecer opções de configuração simplificadas e bons padrões. Ele pode combinar automaticamente seus redutores de fatia, adiciona qualquer middleware Redux que você fornecer, inclui redux-thunk por padrão e permite o uso da extensão Redux DevTools.

#createReducer (): que permite fornecer uma tabela de pesquisa de tipos de ação para funções de redutor de caso, em vez de escrever instruções switch. Além disso, ele usa automaticamente a biblioteca immer para permitir que você escreva atualizações imutáveis ​​mais simples com código mutativo normal, como state.todos [3] .completed = true.

#createAction (): gera uma função de criador de ação para a string de tipo de ação fornecida. A própria função tem toString () definido, para que possa ser usada no lugar da constante de tipo.

#createSlice (): aceita um objeto de funções redutoras, um nome de fatia e um valor de estado inicial, e gera automaticamente um redutor de fatia com criadores de ação e tipos de ação correspondentes.

#createAsyncThunk: aceita uma string de tipo de ação e uma função que retorna uma promessa e gera uma conversão que despacha tipos de ação pendentes / cumpridas / rejeitadas com base nessa promessa

#createEntityAdapter: gera um conjunto de redutores e seletores reutilizáveis ​​para gerenciar dados normalizados na loja

#O utilitário createSelector da biblioteca Reselect, reexportado para facilidade de uso

RTK Query

RTK Query is provided as an optional addon within the @reduxjs/toolkit package. It is purpose-built to solve the use case of data fetching and caching, supplying a compact, but powerful toolset to define an API interface layer for your app. It is intended to simplify common cases for loading data in a web application, eliminating the need to hand-write data fetching & caching logic yourself.

RTK Query is built on top of the Redux Toolkit core for its implementation, using Redux internally for its architecture. Although knowledge of Redux and RTK are not required to use RTK Query, you should explore all of the additional global store management capabilities they provide, as well as installing the Redux DevTools browser extension, which works flawlessly with RTK Query to traverse and replay a timeline of your request & cache behavior.

RTK Query is included within the installation of the core Redux Toolkit package. It is available via either of the two entry points below:

import { createApi } from '@reduxjs/toolkit/query'

/* React-specific entry point that automatically generates
   hooks corresponding to the defined endpoints */
import { createApi } from '@reduxjs/toolkit/query/react'