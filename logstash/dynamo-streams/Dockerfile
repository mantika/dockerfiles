FROM logstash:1.5.6

ENV PATH /opt/logstash/vendor/jruby/bin/:$PATH

RUN curl --create-dirs -sS -o /opt/logstash/vendor/jruby/lib/ruby/.mvn/extensions.xml https://raw.githubusercontent.com/takari/ruby-maven/master/.mvn/extensions.xml

RUN gem install logstash-input-dynamodb logstash-filter-dynamodb

RUN plugin install logstash-input-dynamodb logstash-filter-dynamodb
