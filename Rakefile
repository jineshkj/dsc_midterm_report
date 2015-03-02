
TMP_FILES = [
  '*.aux', '*.idx', '*.out', '*.log', '*.dvi',
  '*.blg', '*.bbl', '*.pdf', '*.ps'
]

PDF_VIEWER = 
  case `uname`
  when /Darwin/
    'open -a Preview'
  when /Linux/
    'evince'
  else
    'echo No viewer for'
  end

task :default => :build

desc "Generate pdf from Latex"
task :build do
  sh "latex latex"
  sh "bibtex latex"
  sh "latex latex"
  sh "latex latex"
  sh "dvips latex -o latex.ps"
  sh "ps2pdf latex.ps latex.pdf"
  
  sh "#{PDF_VIEWER} latex.pdf"
end

desc "Remove temporary files"
task :clean do
  sh "rm -rf #{TMP_FILES.join(' ')}"
end
