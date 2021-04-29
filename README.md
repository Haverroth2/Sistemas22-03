//pacote Pessoa
package sample.model;

//classes abstratas
public abstract class Pessoa {
    private String nome;
    private String cpf;
    private Endereco endereco;

//métodos
    public Pessoa(String nome){
        this.nome = nome;
    }

//get and set
    public Pessoa(String nome, String cpf){
        this.nome = nome;
        this.cpf = cpf;
    }

    public String getNome() {
        return nome;
    }
    public void setNome(String nome) {
        this.nome = nome;
    }
    public String getCpf() {
        return cpf;
    }
    public void setCpf(String cpf) {
        this.cpf = cpf;
    }
    public Endereco getEndereco() {
        return endereco;
    }
    public void setEndereco(Endereco endereco) {
        this.endereco = endereco;
    }
    public void setEndereco(String rua, int numero){
        Endereco endereco = new Endereco();
        endereco.setRua(rua);
        endereco.setNumero(numero);
        this.endereco = endereco;
    }

//to string
    public String toString(){
        return nome
                + ", CPF: "+ cpf
                + "\n" + endereco;
    }
}

//pacote endereço
package sample.model;

//classes abstratas
public class Endereco {
    private String rua;
    private int numero;

//get and set
    public String getRua() {
        return rua;
    }
    public void setRua(String rua) {
        this.rua = rua;
    }
    public int getNumero() {
        return numero;
    }
    public void setNumero(int numero) {
        this.numero = numero;
    }

//sobrecarga to stirng
    @Override
    public String toString() {
        return "Endereco:" + rua +
                ", nº: " + numero;
    }
}

// pacote Pessoa
package sample.model;

//classe importada
public class Cliente extends Pessoa{
    private String email;

//métodos
    public Cliente(String nome) {
        super(nome);
    }
    public Cliente(String nome, String cpf){
        super(nome, cpf);
    }
    public Cliente(String nome, String cpf, String email){
        super(nome, cpf);
        this.email = email;
    }
}

//pacotes importados
package sample;

//pacotes importados
import sample.model.Cliente;
import sample.model.Pessoa;

//classe Main
public class Main{

    public static void main(String[] args) {

//adicioando informações
        Cliente cliente1 = new Cliente("Emílio Santiago");
        cliente1.setCpf("200.900.111-90");
        cliente1.setEndereco("Sete de setembro", 12);
        Cliente cliente2 = new Cliente("Raul Seixas", "888.999.111.90");
        Cliente cliente3 = new Cliente("Dom Pedro I", "1-01", "pedrao@brasil.br");
        System.out.println(cliente1);
        System.out.println(cliente2);
        System.out.println(cliente3);
    }
}

//pacote 
package sample.model;

//classe Produto
public class Produto {
    private String nome;
    private double preco;

//métodos
    public String getNome() {
        return nome;
    }
    public void setNome(String nome) {
        this.nome = nome;
    }
    public double getPreco() {
        return preco;
    }
    public void setPreco(double preco) {
        this.preco = preco;
    }

    public String toString(){
        return nome + ", R$: " + preco;
    }
}

//pacote
package sample.model;

//pacotes importados
import java.util.ArrayList;
import java.util.List;

//classe itens do Pedido
public class ItensDoPedido {
    private List<Produto> produtos;
    private double total;

    public ItensDoPedido(){
        produtos = new ArrayList<>();
    }

//método para retornar
    public double getTotal(){ return  total; }
    public List<Produto> getProdutos(){
        return produtos;
    }
    public void setProduto(String nome, double preco){
        Produto produto = new Produto();
        produto.setNome(nome);
        produto.setPreco(preco);
        this.produtos.add(produto);
        total += preco;

    }

    public void setProduto(Produto produto){
        this.produtos.add(produto);
        total += produto.getPreco();
    }

    public String toString(){
        return produtos + "\nTotal: " + total;
    }}
