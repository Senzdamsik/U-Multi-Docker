FROM node:alpine
WORKDIR "/app"
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build


FROM nginx
EXPOSE 3000
# - Di sini kita hanya mengambil folder "build" saja buat ditaro di nginx karena hanya folder itu yg kita butuhkan di production
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

# - "--from=0" itu maksudnya kita ambil dari "FROM" pertama di atas
COPY --from=0 /app/build /usr/share/nginx/html
