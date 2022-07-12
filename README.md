# NestJS Throttler Redis Storage fo v^3.0.0

![Tests status](https://img.shields.io/github/workflow/status/kkoomen/nestjs-throttler-storage-redis/Tests/master)

Redis storage provider for the [@nestjs/throttler](https://github.com/nestjs/throttler) package.

# Installation

### Yarn

- `yarn add @chienchheung/nestjs-throttler-storage-redis ioredis`

### NPM

- `npm install --save @chienchheung/nestjs-throttler-storage-redis ioredis`

# Usage

```ts
import { ThrottlerModule } from '@nestjs/throttler';
import { ThrottlerStorageRedisService } from '@chienchheung/nestjs-throttler-storage-redis';

@Module({
  imports: [
    ThrottlerModule.forRoot({
      ttl: 60,
      limit: 5,
      storage: new ThrottlerStorageRedisService(),
    }),
  ],
})
export class AppModule {}
```

```ts
import { ThrottlerModule } from '@nestjs/throttler';
import { ThrottlerStorageRedisService } from '@chienchheung/nestjs-throttler-storage-redis';

@Module({
  imports: [
    ThrottlerModule.forRootAsync({
      imports: [ConfigModule],
      inject: [ConfigService],
      useFactory: (config: ConfigService) => ({
        ttl: config.get('THROTTLE_TTL'),
        limit: config.get('THROTTLE_LIMIT'),
        storage: new ThrottlerStorageRedisService(),
      }),
    }),
  ],
})
export class AppModule {}
```

# Issues

Bugs and features related to the redis implementation are welcome in this
repository.

# License

NestJS Throttler Redis Storage is licensed under the MIT license.
