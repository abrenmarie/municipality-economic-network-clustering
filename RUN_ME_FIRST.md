# Как запустить финальную версию проекта

## 1. Что является финальной частью

В проекте есть исследовательский baseline-контур и финальный конкурсный контур.

Исследовательские ноутбуки: `01–11`.

Финальный конкурсный контур:

1. `12_icvi_evaluation.ipynb`
2. `13_method_comparison.ipynb`
3. `14_final_model_125.ipynb`
4. `15_final_visualization.ipynb`

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

В репозитории находятся исходные и подготовленные файлы.

Ключевые подготовленные файлы:

- `features_basic.parquet`
- `features_2024_12.parquet`
- `edges_2024_12.parquet`
- `edges_all_months.parquet`

Исторический baseline:

- `municipality_economic_types.parquet`
- `economic_type_profiles.csv`
- `monthly_economic_type_shares.csv`

Финальная типология:

- `municipality_economic_types_final.parquet`
- `economic_type_profiles_final_125.csv`
- `economic_type_sizes_final_125.csv`
- `economic_type_transitions_final_125.csv`
- `final_model_evaluation.csv`

## 4. Финальный запуск

Для проверки конкурсной версии запускать с чистого Kernel:

1. `12_icvi_evaluation.ipynb`
2. `13_method_comparison.ipynb`
3. `14_final_model_125.ipynb`
4. `15_final_visualization.ipynb`

## 5. Финальная конфигурация

- период: 2023-01 - 2024-12;
- признаки: 5 долей потребления;
- Euclidean distance;
- kNN: 10;
- RBF-веса;
- Louvain: `resolution = 1.25`;
- seed: 42;
- устойчивые экономические типы: K = 3;
- KMeans `n_init = 50`.

Историческая конфигурация `resolution = 1.50` сохраняется как baseline для сравнения.

## 6. Главные результаты

- 50 521 municipality-month наблюдение;
- 24 месяца;
- 3 устойчивых экономических типа;
- Silhouette = 0.3456;
- Calinski-Harabasz = 38 527.26;
- ARI vs resolution 1.50 = 0.8723;
- exact match rate = 95.85%.

## 7. Где лежат результаты

`15_final_visualization.ipynb` создает итоговые графики и автономную HTML Sankey-диаграмму.

`docs/` содержит методологический отчет.

`presentation/` содержит конкурсную презентацию.
