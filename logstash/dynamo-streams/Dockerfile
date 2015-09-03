FROM logstash

ENV PATH /opt/logstash/vendor/jruby/bin/:$PATH

RUN gem install logstash-filter-dynamodb logstash-input-dynamodb

RUN curl --create-dirs -sS -o /opt/logstash/vendor/bundle/jruby/1.9/gems/ruby-maven-3.3.3/.mvn/extensions.xml https://raw.githubusercontent.com/takari/ruby-maven/master/.mvn/extensions.xml

RUN plugin install logstash-filter-dynamodb logstash-input-dynamodb
