# PPLM
## Setup
Usando Python3.6
```bash
pip install -r requirements.txt -f https://download.pytorch.org/whl/torch_stable.html
```
## Pruebas
### Bag of Words

```bash
python run_pplm.py -B military --cond_text "The potato" --length 50 --gamma 1.5 --num_iterations 3 --num_samples 10 --stepsize 0.03 --window_length 5 --kl_scale 0.01 --gm_scale 0.99 --colorama --sample
```
#### Parametros:
1. Stepsize: Nivel del control del tema
2. En caso el texto generado fuese repetitivo: </br>
  a) Reducir `--stepsize` </br>
	b) Incrementar `--kl_scale` (KL-loss coefficient), reducir `--gm_scale` (gm-scaling term) </br>
	c) Agregar `--grad-length xx` (xx = int <= length, e.g. `--grad-length 30`).</br>

### PPLM-Discrim

```bash
python run_pplm.py -D sentiment --class_label 2 --cond_text "My dog died" --length 50 --gamma 1.0 --num_iterations 10 --num_samples 10 --stepsize 0.04 --kl_scale 0.01 --gm_scale 0.95 --sample
```

#### Parametros:
1. Class Label: `--class_label 3` para negativo, and `--class_label 2` para positivo
