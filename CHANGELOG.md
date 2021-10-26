# R2DBC MySQL Changelog

## 0.8.2.RELEASE

### New features

- Added extensions, supports codec registrar.
- Added option `sslHostnameVerifier` of configuration.
- Added `SslContextBuilder` customizer supports.
- Added the TUNNEL into SSL modes.
- Added time zone supports, which contains `ZonedDateTime`, `OffsetDateTime`, `Instant` and `OffsetTime` codec supports.
- Added TCP NoDelay of configuration.
- Added TCP KeepAlive of configuration.

### Features change

- Changed the SSL key and SSL certificate configuration of client.
- Changed the `MySqlConnectionFactoryProvider` when `unixSocket` is set, ignore the host and all SSL options.

### Fixed bugs

- Fixed BOOLEAN (TINYINT(1)) decoding supports.
- Fixed datetime/timestamp microseconds encoding/decoding in text protocol.

## 0.8.1.RELEASE

### New features

- Added client-preparing parametrized statements supporting.
- Added server-preparing simple statements supporting.

### Features change

- Changed parametrized statements to client-preparing.

### Fixed bugs

- Fixed decoding of `AuthChangeMessage`.
- Fixed capabilities for affect rows. Now the count of affect rows is found/touched rows instead of changed rows.

## 0.8.0.RELEASE

### New features

- Added support fetch size for prepared statements.

### Features change

- Changed default type mappings, like `Blob` to `ByteBuffer`, `Clob` to `String`, etc.

### Fixed bugs

- Fixed memory leak when user consumes only a portion of the rows
- Propagated connection closed/killed and emit an exception to subsequent exchanges instead of being hanged.

## 0.8.0.RC2

### New features

- Added support for unix domain socket

### Features change

- Improved support for protocol 3.20 and compatibility for lower version of MySQL

### Fixed bugs

- Fixed capabilities flag with flags mask for remove all unknown flags
- Fixed decoding for distinguish between OK and Prepared OK
- Fixed for drains responded messages when subscriber ignore a entire `Result`
- Fixed exclusion for HTTP/HTTPS modules via Reactor Netty with Revert

## 0.8.0.RC1

### New features

- Added support for `ByteBuffer` encoding and decoding
- Added connection metadata
- Added for drains responded messages when cancel `Result.map` or `getRowsAffected` subscription
- Added support for compound statement
- Added support for special values of `TIME`
- Added exclusions for HTTP/HTTPS modules via Reactor Netty

### Features change

- Minimum options validation via `supports(...)`
- Preferred the default type as `ByteBufer` for `VARBINARY`

### Fixed bugs

- Fixed the encoding for `BigInteger`, should use string encoding instead
- Fixed the capabilities for remove unused flags
- Fixed for against multiple active conversations

## 0.2.0.M2

### New features

- Added support for full authentication phase of *"caching_sha2_password"*
- Added support for SSL and check SSL capabilities that comes from server

### Fixed bugs

- Fixed `ServerVersion` parsing for ignore the postfix of version pattern
- Fixed capabilities for check EOF deprecated flag
