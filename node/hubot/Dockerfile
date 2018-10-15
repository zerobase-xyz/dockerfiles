FROM node

RUN npm install -g yo generator-hubot
RUN npm list -g yo generator-hubot
RUN useradd bot
RUN mkdir /home/bot && chown bot.bot /home/bot

USER bot
WORKDIR /home/bot
RUN  yo hubot --owner "sumir" --name "bot" --description "Hubot image" --adapter slack

CMD cd /home/bot/hubot; bin/hubot --adapter slack
