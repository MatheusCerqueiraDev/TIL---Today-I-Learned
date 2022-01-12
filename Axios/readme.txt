Axios 

Axios é uma ferramenta para receber e postar datas recebidas de um end-point

Axios TypeScript

interface ServerResponse {
  data: ServerData
}

interface ServerData {
  foo: string
  bar: number
}

axios.request<ServerData>({
  url: 'https://example.com/path/to/data',
  transformResponse: (r: ServerResponse) => r.data
}).then((response) => {
  // `response` is of type `AxiosResponse<ServerData>`
  const { data } = response
  // `data` is of type ServerData, correctly inferred
})