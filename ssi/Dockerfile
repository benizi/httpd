FROM httpd:latest
LABEL maintainer "Benjamin R. Haskell <docker@benizi.com>"
RUN sed -i \
  -e '/Indexes Follow/aSSILegacyExprParser on' \
  -e '/Options Indexes/!{ b already }' \
  -e '/Includes/{ b already }' \
  -e 's/Options Indexes/& Includes/' \
  -e :already \
  -e '/ \(include\|cgid\|cgi\)_module/ { b uncomment }' \
  -e '/shtml$/ { b uncomment }' \
  -e b \
  -e :uncomment \
  -e 's/#//' \
  conf/httpd.conf
