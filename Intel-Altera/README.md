# 🛠️ Corrigindo o Erro de Licença do Questa após Instalar o Quartus Prime 23.1

Este tutorial explica como resolver o problema de licença do **Questa Intel FPGA Edition** após instalar o **Quartus Prime 23.1**, onde mesmo com a licença fornecida, o Questa não abre ou impede a simulação de código HDL.

---

## 🔧 Problema

Mesmo após inserir a licença do Questa, o simulador **não inicia** corretamente, impossibilitando o uso para projetos HDL.

---

## ✅ Solução

Você precisa adicionar manualmente a variável de ambiente `LM_LICENSE_FILE` no Windows, apontando para o arquivo `.dat` da licença.

---

## 📝 Instruções Passo a Passo

1. Abra o **Painel de Controle**.
2. Vá em **Sistema** → clique em **Configurações avançadas do sistema**.
3. Na aba **Avançado**, clique em **Variáveis de Ambiente...**.

   ![Aba Avançado](https://github.com/mcleber/Bug_fixes_and_Configuration_Files/blob/main/Intel-Altera/images/aba_avancado.png)

4. Em **Variáveis do sistema**, clique em **Novo...**.
5. Preencha os campos:

   - **Nome da variável:** `LM_LICENSE_FILE`  
   - **Valor da variável:** Caminho completo até o arquivo `.dat` da licença.  
     Exemplo:
     ```
     C:\intelFPGA\23.1\licenses\license.dat
     ```

   ![Exemplo de variável criada](https://github.com/mcleber/Bug_fixes_and_Configuration_Files/blob/main/Intel-Altera/images/variavel_license.png)

6. Clique em **OK** para salvar e **reinicie** o computador ou terminal.

---

## ✅ Resultado Esperado

Após configurar a variável corretamente, o Questa deve abrir normalmente e permitir a simulação de seus projetos.

---

## 📎 Recursos Relacionados

- [Download Quartus Prime 23.1](https://www.intel.com.br/content/www/br/pt/software-kit/795188/intel-quartus-prime-lite-edition-design-software-version-23-1-for-windows.html)
- [Documentação oficial FPGA Intel](https://www.intel.com/content/www/us/en/products/details/fpga.html)

---

