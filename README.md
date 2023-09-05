# Sistema_de_Estoque_simples
Sistema de Estoque criado em C# bem simples


    using System;
    using System.Threading; //Uso da biblioteca Threading para usar a função sleep e conseguir um delay.
    
    class Program
    {
        public static void Main(string[] args)
        {
            //Arrays necessárias. Colocamos um limite de 10 itens para ocupar menos espaço na memória, mas poderia ser feito de forma dinâmica
            string[] estoque = new string[10];
        int[] quantidade = new int[10];
            int[] preco = new int[10];
    int[] total = new int[10];
    
            int soma = 0;
            int a = 0;
            //MENU
            int menu = 0;
            while (menu != 3)
            {
            cheio:
                Console.WriteLine(" 1 - Adicionar itens ao estoque\n 2 - Ver estoque\n 3 - Sair do programa");
                menu = Convert.ToInt32(Console.ReadLine());
                Console.Clear();
                switch (menu)
                {
                    case 1:
    
                    inicio: //Retorna aqui toda vez que usamos a função GOTO
    
                        if (a >= 10)     {
                            Console.WriteLine("!!!AVISO, ESTOQUE CHEIO!!");
                            goto cheio; }
                        //Recebe a entrada de produtos, preços e quantidade
                        Console.WriteLine("Escreva o produto: ");
                        estoque[a] = Console.ReadLine();//Guarda o nome na array estoque em função de 'A' para ir percorrendo as casas do vetor
    
                        Console.WriteLine("Escreva a quantidade do produto: ");
                        quantidade[a] = Convert.ToInt32(Console.ReadLine());//Guarda o nome na array de quantidade
    
                        Console.WriteLine("Escreva o preço do produto: ");
                        preco[a] = Convert.ToInt32(Console.ReadLine());//Guarda o nome na array preco, tive que colocar como int para que assim consiga fazer a multiplicação e dar o valor total
    
                        //Conta realizada para guardar o preço total do produto no estoque e guarda em outra array
                        total[a] = quantidade[a] * preco[a];
    
                        //Mostra o que foi adicionado naquele momento
                        Console.WriteLine($"Adicionado ao estoque \n{quantidade[a]} {estoque[a]}s R${preco[a]}/Un\nTotal: R${total[a]}");
                        Thread.Sleep(3000);
                        Console.Clear();
                        a++;
                        Console.Write("Deseja continuar realizando a digitação? (S/N)"); //Pergunta ao usuário se deseja adicionar mais um item, se não, volta ao menu
                        string resp = Console.ReadLine();
                        if (resp == "S" || resp == "s")
                        {
                            goto inicio;
                        }
                        break;
    
                    case 2:
                        Console.WriteLine("Estoque:");
                        int i = 0;
                        foreach (string item in estoque)//Uso do foreach para colocar apenas as casas da array preenchida
                        {
                            if (!string.IsNullOrEmpty(item))//usado para ignorar as casas em branco, uso do '!' para negar a casa em branco, ou seja, "Escreva as casas que existir informação"
                            {
    
                                Console.WriteLine("Item: " + item);
                                Thread.Sleep(500);
                                Console.WriteLine("Quantidade: " + quantidade[i]);
                                Thread.Sleep(500);
                                Console.WriteLine("Preço: R$" + preco[i]);
                                Thread.Sleep(500);
                                Console.WriteLine("Total: R$" + total[i]);
                                Thread.Sleep(500);
                                Console.WriteLine();
                                i++;
                            }
                        }
                        soma = 0;
                        foreach (int elemento in total)//Novamente uso do foreach para fazer a soma total do estoque e retornar ao usuário
                        {
                            soma += elemento;
                        }
                        Console.WriteLine("Preço total do estoque é " + soma);
                        break;
                }
            }
        }
    }
