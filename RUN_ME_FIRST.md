# Как запустить финальную версию проекта

## 1. Структура

Основные ноутбуки находятся в `notebooks/` и запускаются последовательно:

`01 → 02 → 03 → 04 → 05 → 06 → 07 → 08 → 09 → 10 → 11 → 12 → 13 → 14 → 15`

## 2. Окружение

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

В Windows PowerShell:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

## 3. Данные

Данные и подготовленные модельные файлы включены в репозиторий.
После клонирования проекта проверьте наличие файлов в:

- `data/raw/`
- `data/processed/`

Отдельно загружать данные в обычном сценарии запуска не требуется.

Финальная версия использует следующие подготовленные файлы:

- `features_basic.parquet`
- `features_2024_12.parquet`
- `edges_2024_12.parquet`
- `edges_all_months.parquet`

Финальные результаты сохраняются в `data/processed/`, включая:

- `municipality_economic_types_final.parquet`
- `economic_type_profiles_final_125.csv`
- `economic_type_sizes_final_125.csv`
- `economic_type_transitions_final_125.csv`
- `final_model_evaluation.csv`
- `method_comparison_full.csv`
- `icvi_results_dec2024.csv`
- `louvain_stability_dec2024.csv`

## 4. Финальный прогон

Для конкурсной версии особенно важно запускать с чистого kernel:

1. `12_icvi_evaluation.ipynb`
2. `13_method_comparison.ipynb`
3. `14_final_model_125.ipynb`
4. `15_final_visualization.ipynb`

Это гарантирует, что ICVI, controlled comparison и финальные артефакты построены одной и той же конфигурацией.

## 5. Финальные параметры

Смотреть `configs/config.json`.

Ключевые значения:

- `k = 10`
- Euclidean distance
- RBF weights
- Louvain `resolution = 1.25`
- `seed = 42`
- `K = 3`

## 6. Главные результаты

- 50 521 municipality-month наблюдение
- 24 месяца
- 3 устойчивых экономических типа
- Silhouette = 0.3456
- Calinski-Harabasz = 38 527.26
- ARI vs resolution 1.50 = 0.8723
- Exact match rate = 95.85%

## 7. Артефакты

`15_final_visualization.ipynb` создаёт итоговые графики и интерактивную Sankey-диаграмму.

`docs/` содержит методологический отчёт в DOCX и PDF.

`presentation/` содержит презентацию в PPTX и PDF.
