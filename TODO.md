TODO: Demo Controller + Routing
@Controller('/profile')
@Get, @Post, @Put

@Get('ab\*cd') # wildcard

@Get(':id')
async findOne(@Param('id') id: number)

TODO: DTO (Data Transfer Object)
Basically a class.
Can have superpowers (validation, pipes)
DTO is used with @Body and @Query

TODO: Get data from Body and Query with decorators
@Body() # req.body
@Query() # req.query

@Headers() # req.headers
@Param() # req.params
@Session() # req.session

TODO: Library specific request/response objects
@Req() request: Request
@Res() response: Response

TODO: Use decorators to modify response.
@Header('Cache-Control', 'None')
@HttpCode(204) # status code
@Redirect('https://...', 301)

TODO: Configure in Module
@Module({controllers: [ProfileController]})

TODO: Validation Pipes
ParseIntPipe, ParseUUIDPipe, ParseEnumPipe
https://docs.nestjs.com/pipes
async findOne(@Param('id', ParseIntPipe) id: number)

TODO: Implement guards
https://docs.nestjs.com/guards

TODO: Implement exceptions and exception filters
Raise: throw new HttpException('Forbidden', HttpStatus.FORBIDDEN)
Local: @UseFilters(new HttpExceptionFilter())
Global: app.useGlobalFilters(new HttpExceptionFilter());

```ts
export class MissingUserException extends HttpException {
  constructor() {
    super('User not found', HttpStatus.NOT_FOUND)
  }
}

@Catch(HttpException)
export class HttpExceptionFilter implements ExceptionFilter {
  catch(exception: HttpException, host: ArgumentsHost) {
    const ctx = host.switchToHttp()
    const response = ctx.getResponse<Response>()
    const request = ctx.getRequest<Request>()
    const status = exception.getStatus()

    response.status(status).json({
      statusCode: status,
      timestamp: new Date().toISOString(),
      path: request.url,
    })
  }
}
```
