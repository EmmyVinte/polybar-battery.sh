# polybar-battery.sh
Um tutorial completo de iniciante para iniciante de como monitorar a bateria de seu notebook pela polybar com bspwm.
![image](https://user-images.githubusercontent.com/117837570/229532231-855892cc-ee18-443e-a229-9e199914cd0d.png)
![image](https://user-images.githubusercontent.com/117837570/229534120-4e9df9e6-bb7c-4112-8b4a-0e8106d53576.png)

## Funcionamento
O Script muda os ícones de acordo com a porcentagem da bateria, também possui um ícone específico para quando estiver carregando.

## Passo 1
Faça download de **polybar-battery.sh**, mova o arquivo *battery.sh* para dentro da pasta de scripts na poybar, geralmente fica em:
  ```bash
  ~/.config./polybar/scripts/battery.sh
  ```
  - Caso não tenha a pasta, crie uma!

## Passo 2
Dê permissão de execução ao arquivo com o comando:
  ```bash
  chmod +x /caminho/do/arquivo/battery.sh
  ```
  ### Passo 2.1 (*battery.sh, linha 5 e 8*)
  Em meu notebook, o local onde consigo extrair informações da bateria são esses:
  - /sys/class/power_supply/ADP1/online (Valor em binário de 'Carregando' ou 'Descarregando')
  - /sys/class/power_supply/BAT1/capacity (Número relativo a % da bateria)
  
  É importante que você procure o local correto em seu dispositivo e substitua essas linhas!
  Dentro do arquivo battery.sh deixei mais informações relevantes, dê uma olhada!

## Passo 3
Abra o arquivo de configuração de sua polybar e adicione essas linhas:
  ```bash
  [module/battery]
  type = custom/script
  exec = /bin/bash -c 'caminho/do/arquivo/battery.sh'
  interval = 1
  format-prefix-foreground = ${colors.primary}
  format-args = <label>
  label = %output%
  ```

Lembre-se de substituir o caminho pelo correto!
Lembre-se de adicionar o módulo *battery.sh* em sua polybar para ser mostrado!
  - Exemplo:
  ```bash
  modules-left = xworkspaces
  modules-right = cpu memory battery
  ```
    
## Passo 4
Reinicie sua polybar com o comando:
  ```bash
  polybar example -r &
  ```
Caso já esteja em execução, primeiro mate o processo e rode novamente com os comandos:
  ```bash
  ps aux | grep polybar
  ```
  ```bash
  kill PID (Substitua o PID pelo número do processo)
  ```
  ```bash
  polybar example -r &
  ```
## Nota final
Recomendo que abra e visualize o arquivo *battery.sh* para poder customizá-lo a seu sabor.
Não disponibilizo suporte a esse arquivo!
