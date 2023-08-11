FROM thevlang/vlang:alpine as build

WORKDIR /app

{{#files}}
  COPY '{{source}}' '{{target}}'
{{/files}}

{{#bootstrap}}
  RUN {{{.}}}
{{/bootstrap}}

RUN v . -prod -o server

FROM alpine

WORKDIR /app

COPY --from=build /app /app

CMD {{command}}