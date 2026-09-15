# Desafio-os-
import os 
import subprocess 
# ---------- ARQUIVOS ---------
# 1) Criar arquivo 
# API: open()  |  Syscall do SO: 

open()/creat() arquivo = "dados.txt" 
open(arquivo, "w").close() 
print(f"[Arquivos] Arquivo '{arquivo}' criado.")

# 2) Escrever e ler dados 
# API: write() / read()  |  Syscall do SO: write() e read() 

with open(arquivo, "w") as f:    
f.write("Ola, mundo!") 
with open(arquivo, "r") as f:    
	conteudo = f.read() 
	print(f"[Arquivos] Conteudo lido do arquivo: {conteudo}") 
# ---------- DIRETORIOS ---------
# 3) Criar e listar diretorio 
# API: os.mkdir() / os.listdir()  |  Syscall do SO: mkdir() e readdir() 

pasta = "minha_pasta" if not os.path.exists(pasta):    
os.mkdir(pasta) 
	print(f"[Diretorios] Diretorio '{pasta}' criado.") 
	print(f"[Diretorios] Conteudo da pasta atual: {os.listdir('.')}") 
# ---------- PROCESSOS ---------
# 4) Obter proprio PID 
# API: os.getpid()  |  Syscall do SO: getpid()

meu_pid = os.getpid() 
print(f"[Processos] PID do processo atual: {meu_pid}") 

# 5) Criar outro processo e aguardar sua finalizacao 
# API: subprocess.Popen() / .wait()  |  Syscall do SO: fork()+exec() e waitpid() 

processo = subprocess.Popen(["python3", "-c", "print('Ola do processo filho!')"]) 
processo.wait()
	print(f"[Processos] Processo filho (PID {processo.pid}) finalizado.")
