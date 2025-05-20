programa
{
    inclua biblioteca Texto

    cadeia nome[10], curso[10], turnoAluno[10], nome_r[10], endereco[10]
    cadeia emailA[10], email_r[10]
    cadeia telefone[10], telefone_r[10], num_matricula[10]
    inteiro idade[10], i, opcao[10]

    funcao Dados(inteiro i)
    {
        escreva("Informe seu nome: ")
        leia(nome[i])

        escreva("Informe sua idade: ")
        leia(idade[i])

        enquanto (idade[i] < 0 ou idade[i] > 100)
        {
            escreva("\nIdade Inválida\n")
            escreva("Informe sua idade novamente: ")
            leia(idade[i])
        }

        se (idade[i] < 18)
        {
            escreva("Informe o nome do seu responsável: ")
            leia(nome_r[i])
            escreva("Informe o e-mail do seu responsável: ")
            leia(email_r[i])
            email_r[i] = validarEmail(email_r[i])
            escreva("Informe o número de telefone do seu responsável: ")
            leia(telefone_r[i])
        }

        // Verificação de matrícula única
        inteiro j, repetido
        repetido = 1

        enquanto (repetido == 1)
        {
            repetido = 0
            escreva("Informe o número da matrícula: ")
            leia(num_matricula[i])

            para (j = 0; j < i; j++)
            {
                se (num_matricula[i] == num_matricula[j])
                {
                    escreva("\nMatrícula já cadastrada. Por favor, informe um número de matrícula diferente.\n")
                    repetido = 1
                }
            }
        }

        escreva("Informe o seu email: ")
        leia(emailA[i])
        emailA[i] = validarEmail(emailA[i])

        maisDados(i)
    }

    funcao cadeia validarEmail(cadeia a)
    {
        inteiro ValA, ValP

        ValA = Texto.posicao_texto("@", a, 0)
        ValP = Texto.posicao_texto(".com", a, 0)

        enquanto (ValA < 0 ou ValP < 0)
        {
            escreva("\nFormato de Email inválido, o email deve conter '@' e '.com'\n")
            escreva("Informe o email novamente: ")
            leia(a)
            ValA = Texto.posicao_texto("@", a, 0)
            ValP = Texto.posicao_texto(".com", a, 0)
        }

        retorne a
    }

    funcao maisDados(inteiro i)
    {
        escreva("Informe seu número de telefone: ")
        leia(telefone[i])

        escreva("Informe seu endereço: ")
        leia(endereco[i])

        escreva("Informe o curso desejado: ")
        leia(curso[i])

        escreva("Escolha o seu turno:\n")
        escreva("1 - Matutino\n2 - Vespertino\n3 - Noturno\n")
        leia(opcao[i])

        turnoAluno[i] = obterTurno(opcao[i])

        enquanto (turnoAluno[i] == "0")
        {
            escreva("\nOpção Inválida. Escolha novamente:\n")
            escreva("1 - Matutino\n2 - Vespertino\n3 - Noturno\n")
            leia(opcao[i])
            turnoAluno[i] = obterTurno(opcao[i])
        }

        confirmarDados(i)
    }

    funcao cadeia obterTurno(inteiro opcao)
    {
        se (opcao == 1)
            retorne "Matutino"
        senao se (opcao == 2)
            retorne "Vespertino"
        senao se (opcao == 3)
            retorne "Noturno"
        senao
        {
            escreva("\nOpção Inválida\n")
            retorne "0"
        }
    }

    funcao confirmarDados(inteiro i)
    {
    	   escreva("------------------\n")
        escreva("CONFIRA SEUS DADOS:\n")
        escreva("------------------\n")
        escreva("Nome: ", nome[i], "\n")
        escreva("Idade: ", idade[i], "\n")
        escreva("E-mail: ", emailA[i], "\n")
        escreva("Endereço: ", endereco[i], "\n")
        escreva("Telefone: ", telefone[i], "\n")
        escreva("Número da Matrícula: ", num_matricula[i], "\n")
        escreva("Curso: ", curso[i], "\n")
        escreva("Turno: ", turnoAluno[i], "\n")

        se (idade[i] < 18)
        {
            escreva("Nome do responsável: ", nome_r[i], "\n")
            escreva("Email do responsável: ", email_r[i], "\n")
            escreva("Telefone do responsável: ", telefone_r[i], "\n")
        }
    }

    funcao inicio()
    {
        inteiro op
        escreva("-----------------------\n")
        escreva("SEJA BEM-VINDO AO SENAI\n")
        escreva("-----------------------\n")
        escreva("1 - Para continuar o cadastro\n")
        escreva("2 - Para sair da página\n")
        escreva("Digite o número: ")
        leia(op)

        se (op == 2)
        {
            escreva("\nOk, até a próxima!!!\n")
        }
        senao se (op == 1)
        {
            para(i = 0; i < 2; i++)
            {
                escreva("\n-------- Preencha os dados a seguir --------\n")
                Dados(i)
            }
        }
        senao
        {
        	
            enquanto (op < 1 ou op > 2)
            {
                escreva("\nOpção Inválida. Escolha novamente:\n")
                escreva("1 - Para continuar o cadastro\n")
                escreva("2 - Para sair da página\n")
                leia(op)
            }

            se (op == 1)
            {
                para(i = 0; i < 2; i++)
                {
                    escreva("\n-------- Preencha os dados a seguir --------\n")
                    Dados(i)
                }
            }
            senao
            {
                escreva("\nOk, até a próxima!\n")
            }
        }
    }
}
