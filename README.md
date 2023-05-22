# Trabalho_3_PC2


``` Java

import java.util.Scanner;

public class Aluno {
    private Integer matricula;
    private String nome;
    private Double[] notas;

    public Aluno(Integer matricula, String nome, int quantidadeNotas) {
        this.matricula = matricula;
        this.nome = nome;
        this.notas = new Double[quantidadeNotas];
    }

    public Integer getMatricula() {
        return matricula;
    }

    public String getNome() {
        return nome;
    }

    public Double[] getNotas() {
        return notas;
    }

    public void setNotas(Double[] notas) {
        this.notas = notas;
    }
}

public class Diario {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Criação do array para armazenar os alunos
        Aluno[] alunos = new Aluno[100]; // Supondo um máximo de 100 alunos

        int quantidadeAlunos = 0;

        // Leitura dos alunos e notas fornecidos pelo usuário
        System.out.println("Digite a matrícula, nome do aluno e quantidade de notas (digite 0 para encerrar):");
        Integer matricula = scanner.nextInt();

        while (matricula != 0) {
            scanner.nextLine(); // Limpar o buffer do scanner

            String nome = scanner.nextLine();
            int quantidadeNotas = scanner.nextInt();
            Double[] notas = new Double[quantidadeNotas];

            for (int i = 0; i < quantidadeNotas; i++) {
                notas[i] = scanner.nextDouble();
            }

            Aluno aluno = new Aluno(matricula, nome, quantidadeNotas);
            aluno.setNotas(notas);

            alunos[quantidadeAlunos] = aluno;
            quantidadeAlunos++;

            System.out.println("Digite a matrícula, nome do aluno e quantidade de notas (digite 0 para encerrar):");
            matricula = scanner.nextInt();
        }

        // Exibição da lista de alunos com notas e médias
        System.out.println("Lista de Alunos:");
        for (int i = 0; i < quantidadeAlunos; i++) {
            Aluno aluno = alunos[i];
            Double[] notas = aluno.getNotas();

            System.out.println("Matrícula: " + aluno.getMatricula());
            System.out.println("Nome: " + aluno.getNome());
            System.out.print("Notas: ");
            for (Double nota : notas) {
                System.out.print(nota + " ");
            }
            System.out.println();

            Double media = calcularMedia(notas);
            System.out.println("Média: " + media);
            System.out.println();
        }
    }

    public static Double calcularMedia(Double[] notas) {
        double soma = 0;
        for (Double nota : notas) {
            soma += nota;
        }
        return soma / notas.length;
    }
}


```
