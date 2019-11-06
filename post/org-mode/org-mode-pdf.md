
mac下如何配置 org-mode 才能输出中文的pdf？

来自群聊中

可以用xelatex

或者

```
;; latex 支持中文
(require 'ox)
(require 'ox-html)
(require 'ox-publish)

(add-to-list 'org-latex-classes '("pdf" "\\documentclass[fontset = mac]{ctexart}
[NO-DEFAULT-PACKAGES]
\\usepackage[colorlinks,linkcolor=black,anchorcolor=black,
             citecolor=black]{hyperref}
\\usepackage[top=3truecm,bottom=2.5truecm,
            left=1.1truecm,right=1.1truecm,
            bindingoffset=1.0truecm,
            headsep=1.6truecm,
            footskip=1.5truecm,
            headheight=15pt    % 标准中没有要求页眉的高度，这里设置成
                               % 15pt 了
           ]{geometry}
\\setCJKmainfont[BoldFont={Microsoft YaHei},ItalicFont={Microsoft YaHei}]{Microsoft YaHei}
"
                  ("\\section{%s}" . "\\section*{%s}")
                  ("\\subsection{%s}" . "\\subsection*{%s}")
                  ("\\subsubsection{%s}" . "\\subsubsection*{%s}")
                  ("\\paragraph{%s}" . "\\paragraph*{%s}")
                  ("\\subparagraph{%s}" . "\\subparagraph*{%s}")))

(setq org-latex-default-class "pdf")

(setq org-latex-pdf-process
      '(
        "xelatex -interaction nonstopmode -output-directory %o %f"
        "xelatex -interaction nonstopmode -output-directory %o %f"
        "xelatex -interaction nonstopmode -output-directory %o %f"
        "rm -fr %b.out %b.log %b.tex auto"
        ))

(defun peng-use-xelatex ()
  (interactive)
  (let* ((tempfile
      (file-name-base))) (progn (shell-command (concat "rm -rf " tempfile
                               ".bbl " tempfile ".blg " tempfile ".out " tempfile ".log " tempfile
                               ".aux " tempfile ".toc" tempfile ".pdf"))
                    (compile (concat "xelatex "
                             (concat tempfile ".tex")
                             (concat ";rm -rf " tempfile ".bbl " tempfile
                                 ".blg " tempfile ".out " tempfile ".log " tempfile ".aux " tempfile
".toc" ";open " tempfile ".pdf"))))))
```
