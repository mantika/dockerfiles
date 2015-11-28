FROM logstash:1.5.5

ENV PATH /opt/logstash/vendor/jruby/bin/:$PATH

RUN curl --create-dirs -sS -o /opt/logstash/vendor/jruby/lib/ruby/.mvn/extensions.xml https://raw.githubusercontent.com/takari/ruby-maven/master/.mvn/extensions.xml

RUN gem install logstash-filter-dynamodb logstash-input-dynamodb


RUN plugin install logstash-filter-dynamodb logstash-input-dynamodb
