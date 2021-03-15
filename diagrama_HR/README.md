# Diagrama de Hertzsprung-Russell

![alt_text](https://github.com/marcoaurelioguerrap/aleatorios/blob/main/diagrama_HR/imagens/freq_estrelas.png)
![alt_text](https://github.com/marcoaurelioguerrap/aleatorios/blob/main/diagrama_HR/imagens/cor_estrelas.png)

Código para fazer o diagrama de Luminosidade vs temperatura de uma estrela os dados foram retirados do site do [banco de dados de estrelas Gaia2](https://gea.esac.esa.int/archive/) , não sou astronomo fiz esse grafico por que acho ele bonito. Usei como guia o artigo [***Gaia*** **Data Release 2** - Observational Hertzsprung-Russell diagrams](https://www.aanda.org/articles/aa/full_html/2018/08/aa32843-18/aa32843-18.html#S3) nele tem o query para pegar os dados.

3 milhões de estrelas ( e 212728 de estrelas se utilizar parallax > 10, o gráfico de cor fica mais bonito assim )

>SELECT phot_g_mean_mag+5*log10(parallax)-10 AS mg, bp_rp FROM gaiadr2.gaia_source
WHERE parallax_over_error > 10
AND phot_g_mean_flux_over_error>50
AND phot_rp_mean_flux_over_error>20
AND phot_bp_mean_flux_over_error>20
AND phot_bp_rp_excess_factor < 1.3+0.06*power(phot_bp_mean_mag-phot_rp_mean_mag,2)
AND phot_bp_rp_excess_factor > 1.0+0.015*power(phot_bp_mean_mag-phot_rp_mean_mag,2)
AND visibility_periods_used>8
AND astrometric_chi2_al/(astrometric_n_good_obs_al-5)<1.44*greatest(1,exp(-0.4*(phot_g_mean_mag-19.5)))
\\*AND parallax > 10 
