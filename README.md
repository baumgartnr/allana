package projetoFinal;

import java.util.ArrayList;
import java.util.List;

public class Matricula {

    private Aluno aluno;
    private Disciplina disciplina;
    private Turma turma;
    private StatusMatricula status;
    private List<Nota> notas = new ArrayList<>();

    public Matricula(Aluno aluno, Disciplina disciplina, Turma turma,
                     StatusMatricula status, List<Nota> notas) {
        this.aluno = aluno;
        this.disciplina = disciplina;
        this.turma = turma;
        this.status = status;
        this.notas = notas;
    }

    public void cancelar() {
        this.status = StatusMatricula.CANCELADA;
        System.out.println("Sua matrícula foi cancelada com sucesso");
    }

    public void adicionarNota(Nota nota) {
        notas.add(nota);
    }

    public List<Nota> listarNotas() {
        return notas;
    }

    public List<Nota> getNotas() {
        return notas;
    }
}
package projetoFinal;

import java.util.ArrayList;
import java.util.List;

public class Aluno extends Pessoa {
    
    private  List<Matricula>  matriculas = new ArrayList<>();
    
	public Aluno(String nome, String cpf, int idade, String email, List<Matricula> matriculas) {
		super(nome, cpf, idade, email);
		this.matriculas = matriculas;
	}


	public void adicionarMatricula(Matricula matricula) {
    	if(matricula != null) {
    		matriculas.add(matricula);
    	}
    };
    
    public List<Nota> consultarNotas(){
    	List<Nota> todas = new ArrayList<>();
    	for (Matricula m : matriculas) {
    		todas.addAll(m.getNotas());
    	}
    	return todas;
    }
    
    
    public void gerarBoleto(double valor) {
    	Boleto boleto = new Boleto(valor, false);
    	boleto.gerar();
    }

}
