# slim系のnodeから構築することを定義
FROM node:lts-bullseye-slim AS base
# コンテナ内の作業ディレクトリを作成
WORKDIR /app
# パッケージ一覧(インデックス)を更新
RUN apt update \
    && yarn install
# ポート番号5173でコンテナを公開

COPY ./front .

COPY docker/front/entrypoint.sh /

RUN chmod +x /entrypoint.sh

EXPOSE 5173

# 開発用環境
FROM base AS dev

CMD ["/bin/bash"]
# 本番環境用
# FROM nginx:stable-alpine as prod

# COPY --from=base /app/dist /usr/share/nginx/html


# CMD ["nginx", "-g", "daemon off;"]