# sistema-para-alunos-de-academia
Sistema para cadastro e controle de alunos de academia

# FUNCIONALIDADES:
# 1.Cadastrar alunos(nome,peso,plano mensal)
# 2.Buscar alunos cadastrados no banco de dados
# 3.Login do funcionário com senha

# def cadastrar_aluno():
    global dados
    while True:
        from datetime import date,timedelta
        from random import randint
        ID = randint(1000,9999)
        print(f'O id  gerado para  aluno é {ID}')
        Aluno = input(str('NOME :   ')).capitalize()
        print('QUAL SERÁ O PLANO DE ESCOLHA?',
              'MENSAL : 30 DIAS - 150$',
              'TRIMESTRAL : 90 DIAS - 400$',
              'ANUAL : 12 MESES - 1200$')
        plano = input(' ').upper()
        if plano== 'MENSAL':
            hoje = date.today()
            data = hoje + timedelta(days = 30)#adicionar30 dias de agora
            print(f'A data de vencimento é {data}')
        elif plano == 'TRIMESTRAL':
            hoje = date.today()
            data = hoje + timedelta(days= 90)
            print(f'A data de vencimento é {data}')
        elif plano == 'ANUAL':
            hoje = date.today()
            data = hoje + timedelta(days = 360)
            print (f'A data de vencimento é {data}')
        peso = float(input('Digite o peso do aluno: '))
        idade = int(input('Digite a idade do aluno: '))
        status = 'ATIVO'
        dados = {'ID':ID,'nome':Aluno,
                  'plano escolhido':plano,
                  'peso':peso,'idade': idade,
                 'status': 'ATIVO' }
        lista_alunos.append(dados)

        return { 'nome' : Aluno ,
                 'idade' :idade,
                 'plano' : plano }


# def login_funcionário():
    funcionarios_da_empresa = ['Kate', 'Anthony']
    nome = input('Login do funcionário: ').capitalize()
    if nome not in funcionarios_da_empresa:
        print('NENHUM FUNCIONÁRIO COM ESTE NOME ESTÁ CADASTRADO')
        while True:
            senha = input('USUÁRIO NÃO IDENTIFICADO,DIGITE A SENHA: ')
            if senha != '1234':
                print('ACESSO NEGADO')
            else:
                break


# def consultar_alunos():
   print(lista_alunos)

# def pesquisar_aluno():
    compativeis =[]
    nome_pesquisado = input(str('Qual o aluno que deseja buscar?'))
    for aluno in lista_alunos:
       if nome_pesquisado == aluno['nome']:
            compativeis.append(aluno)
    if compativeis :
        print (compativeis)
    else:
        print('NÃO HÁ ALUNOS COMPATÍVEIS COM A PESQUISA')




lista_alunos = []
while True:
    print('-MENU PRINCIPAL-'
           'O QUE DESEJA FAZER?'
           '[1] CADASTAR ALUNO'
           '[2] CONSULTAR ALUNOS'
           '[3] PESQUISAR ALUNO')
    menu = str(input('  '))
    if menu == '1':
        login_funcionário()
        cadastrar_aluno()
    elif menu == '2':
        login_funcionário()
        consultar_alunos()
    elif menu == '3':
        login_funcionário()
        pesquisar_aluno()
