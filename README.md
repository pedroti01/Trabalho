public class Aluno {
    private String nome;
    private String matricula;
    private String sexo;
    private String dataNascimento;
    private String curso;
    private int anoInicio;
    private double notaProva1;
    private double notaProva2;
    private double mediaTrabalhos;

    // Getters e Setters
    public String getNome() {
        return nome;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public String getMatricula() {
        return matricula;
    }

    public void setMatricula(String matricula) {
        this.matricula = matricula;
    }

    public String getSexo() {
        return sexo;
    }

    public void setSexo(String sexo) {
        this.sexo = sexo;
    }

    public String getDataNascimento() {
        return dataNascimento;
    }

    public void setDataNascimento(String dataNascimento) {
        this.dataNascimento = dataNascimento;
    }

    public String getCurso() {
        return curso;
    }

    public void setCurso(String curso) {
        this.curso = curso;
    }

    public int getAnoInicio() {
        return anoInicio;
    }

    public void setAnoInicio(int anoInicio) {
        this.anoInicio = anoInicio;
    }

    public double getNotaProva1() {
        return notaProva1;
    }

    public void setNotaProva1(double notaProva1) {
        this.notaProva1 = notaProva1;
    }

    public double getNotaProva2() {
        return notaProva2;
    }

    public void setNotaProva2(double notaProva2) {
        this.notaProva2 = notaProva2;
    }

    public double getMediaTrabalhos() {
        return mediaTrabalhos;
    }

    public void setMediaTrabalhos(double mediaTrabalhos) {
        this.mediaTrabalhos = mediaTrabalhos;
    }

    // Método para calcular a média final
    public double calcularMediaFinal() {
        return (notaProva1 + notaProva2 + mediaTrabalhos) / 3;
    }

    // Método para verificar se o aluno está aprovado
    public boolean isAprovado() {
        return calcularMediaFinal() >= 6;
    }
}import java.util.Scanner;

public class AlunoTeste {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Aluno aluno = new Aluno();

        System.out.println(">>> INÍCIO SOFTWARE ALUNO <<<");

        // Entrada de dados do aluno
        System.out.print("Informe o nome do aluno: ");
        aluno.setNome(scanner.nextLine());

        System.out.print("Informe a matrícula: ");
        aluno.setMatricula(scanner.nextLine());

        System.out.print("Informe o sexo: ");
        aluno.setSexo(scanner.nextLine());

        System.out.print("Informe a data de nascimento: ");
        aluno.setDataNascimento(scanner.nextLine());

        System.out.print("Informe o curso: ");
        aluno.setCurso(scanner.nextLine());

        System.out.print("Informe o ano de início: ");
        aluno.setAnoInicio(scanner.nextInt());

        System.out.print("Informe a Nota da Prova 1: ");
        aluno.setNotaProva1(scanner.nextDouble());

        System.out.print("Informe a Nota da Prova 2: ");
        aluno.setNotaProva2(scanner.nextDouble());

        System.out.print("Informe a média dos Trabalhos: ");
        aluno.setMediaTrabalhos(scanner.nextDouble());

        // Exibição das informações e do resultado
        System.out.println("### INFORMAÇÕES ###");
        System.out.println("Nome: " + aluno.getNome());
        System.out.println("Matrícula: " + aluno.getMatricula());
        System.out.println("Nome do curso: " + aluno.getCurso());

        double mediaFinal = aluno.calcularMediaFinal();
        String situacao = aluno.isAprovado() ? "Aprovado" : "Reprovado";
        System.out.printf("Situação: %s com média %.2f\n", situacao, mediaFinal);

        System.out.println(">>> Fim da execução do software <<<");

        scanner.close();
    }
}>>> INÍCIO SOFTWARE ALUNO <<<
Informe o nome do aluno: Seu Madruga
Informe a matrícula: 123456
Informe o sexo: M
Informe a data de nascimento: 07/08/1990
Informe o curso: Economia
Informe o ano de início: 2024
Informe a Nota da Prova 1: 6.00
Informe a Nota da Prova 2: 7.00
Informe a média dos Trabalhos: 8.00
### INFORMAÇÕES ###
Nome: Seu Madruga
Matrícula: 123456
Nome do curso: Economia
Situação: Aprovado com média 7.00
>>> Fim da execução do software <<<
