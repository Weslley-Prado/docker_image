# Estágio do construtor
FROM golang:1.17-alpine AS builder

WORKDIR /app

# Inicialize o módulo Go
RUN go mod init fullcycle

# Copie o código fonte
COPY . .

# Construa o aplicativo Go
RUN go build -o main .

# Estágio final
FROM scratch

WORKDIR /app

# Copie o binário do estágio do construtor para o estágio final
COPY --from=builder /app/main .

# Comando padrão a ser executado quando o contêiner for iniciado
CMD ["./main"]
