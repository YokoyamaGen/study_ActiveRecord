# study_ActiveRecord

以下、問題演習における回答を作成<br>
https://www.tech-essentials.work/courses/50/tasks/28

- 従業員番号が499999の従業員の給料全てを取得してください
  - Salary.where(emp_no: 499999)
  
- 従業員番号が499999の従業員の2001-01-01時点の給料を取得してください
  - Salary.where("emp_no = ? and from_date < ? and ? < to_date",  499999, "2001-01-01", "2001-01-01")
  
- 150000以上の給料をもらったことがある従業員の一覧を取得してください
  - Employee.joins(:salaries).where("salary > ?", 150000).distinct
  
- 150000以上の給料をもらったことがある女性従業員の一覧を取得してください
  - Employee.joins(:salaries).where("salary > ? AND gender = ?", 150000, "F").distinct
  
- どんな肩書きがあるか一覧で取得してきてください
  - Title.select(:title).distinct
  
- 2000-1-29以降に肩書きが「Technique Leader」になった従業員を取得してください
  - Employee.joins(:titles).merge(Title.where("title = ? AND from_date >= ?", "Technique Leader", "2000-01-29"))
  
- 部署番号がd001である部署のマネージャー歴代一覧を取得してきてください
  
