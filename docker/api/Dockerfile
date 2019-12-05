FROM ruby:2.6.3

ENV RAILS_ROOT /var/www/your-bundle
RUN mkdir -p $RAILS_ROOT

WORKDIR $RAILS_ROOT

COPY server/Gemfile Gemfile
COPY server/Gemfile.lock Gemfile.lock

RUN gem install bundler
RUN gem install nokogiri -v '1.10.4'
RUN gem install nio4r -v '2.5.2'
RUN gem install websocket-driver -v '0.7.1'
RUN gem install bindex -v '0.8.1'
RUN gem install msgpack -v '1.3.1'
RUN gem install bootsnap -v '1.4.5'
RUN gem install byebug -v '11.0.1'
RUN gem install ffi -v '1.11.1'
RUN gem install mini_racer -v '0.2.6'
RUN gem install pg -v '1.1.4'
RUN gem install puma -v '3.12.1'

RUN bundle lock --add-platform x86-mingw32 x86-mswin32 x64-mingw32 java
RUN bundle install
RUN bundle update

COPY server .

#RUN rspec
#EXPOSE 5000

ENV RAILS_ENV='production'
ENV RACK_ENV='production'

CMD ["rails", "s", "-p", "5000"]