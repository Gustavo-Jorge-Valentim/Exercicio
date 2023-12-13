import java.util.ArrayList;
import java.util.Date;
import java.util.List;

public class Paciente {
    private String nome;
    private String dataNascimento;
    private String endereco;
    private String telefone;
    private int numeroRegistro;

    public Paciente(String nome, String dataNascimento, String endereco, String telefone) {
        this.nome = nome;
        this.dataNascimento = dataNascimento;
        this.endereco = endereco;
        this.telefone = telefone;
        this.numeroRegistro = gerarNumeroRegistroUnico();
    }

    private int gerarNumeroRegistroUnico() {
        return /* lógica */;
    }
}

public class Medico {
    private String nome;
    private String especialidade;
    private int numeroRegistro;

    public Medico(String nome, String especialidade) {
        this.nome = nome;
        this.especialidade = especialidade;
        this.numeroRegistro = gerarNumeroRegistroUnico();
    }

    private int gerarNumeroRegistroUnico() {
        return /* lógica */;
    }
}

public class Consulta {
    private Medico medico;
    private Paciente paciente;
    private Date dataHora;
    private boolean disponivel;

    public Consulta(Medico medico, Date dataHora) {
        this.medico = medico;
        this.dataHora = dataHora;
        this.disponivel = true;
    }
}

public class Prontuario {
    private Paciente paciente;
    private Medico medico;
    private String historico;
    private List<String> prescricoes;

    public Prontuario(Paciente paciente, Medico medico) {
        this.paciente = paciente;
        this.medico = medico;
        this.historico = "";
        this.prescricoes = new ArrayList<>();
    }
}

public class AtendimentoClinico {
    private List<Consulta> consultasDisponiveis;

    public AtendimentoClinico() {
        this.consultasDisponiveis = new ArrayList<>();
    }

    public List<Medico> listarMedicosDisponiveis() {
        return /* lista de médicos */;
    }

    public List<Consulta> consultarConsultasDisponiveis(Medico medico) {
        return /* lista de consultas */;
    }

    public boolean marcarConsulta(Paciente paciente, Consulta consulta) {
        return /* true se a consulta for marcada com sucesso */;
    }

    public Prontuario criarProntuario(Paciente paciente, Medico medico) {
        return /* prontuário criado */;
    }

    public void adicionarHistorico(Prontuario prontuario, String historico) {
    }

    public void adicionarPrescricao(Prontuario prontuario, String prescricao) {
    }
}

public class Main {
    public static void main(String[] args) {
        Paciente paciente = new Paciente("João", "1990-05-15", "Rua A, 123", "999999999");
        Medico medico = new Medico("Dr. Maria", "Cardiologia");

        AtendimentoClinico atendimentoClinico = new AtendimentoClinico();

        System.out.println("Médicos disponíveis:");
        for (Medico m : atendimentoClinico.listarMedicosDisponiveis()) {
            System.out.println("- " + m.getNome() + " - Especialidade: " + m.getEspecialidade());
        }

        System.out.println("\nConsultas disponíveis para " + medico.getNome() + ":");
        for (Consulta consulta : atendimentoClinico.consultarConsultasDisponiveis(medico)) {
            System.out.println("- Data/Hora: " + consulta.getDataHora());
        }

        Consulta consultaMarcada = new Consulta(medico, new Date());
        boolean consultaMarcadaComSucesso = atendimentoClinico.marcarConsulta(paciente, consultaMarcada);

        if (consultaMarcadaComSucesso) {
            System.out.println("\nConsulta marcada para " + paciente.getNome() + " com sucesso!");
        } else {
            System.out.println("\nFalha ao marcar consulta para " + paciente.getNome() + ". Consulta indisponível.");
        }

        Prontuario prontuario = atendimentoClinico.criarProntuario(paciente, medico);

        atendimentoClinico.adicionarHistorico(prontuario, "Paciente apresentou sintomas de...");
        atendimentoClinico.adicionarHistorico(prontuario, "Exames realizados: ...");

        atendimentoClinico.adicionarPrescricao(prontuario, "Medicação: ...");
        atendimentoClinico.adicionarPrescricao(prontuario, "Recomendação: ...");
    }
}
