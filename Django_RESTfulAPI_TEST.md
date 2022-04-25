# Django Restful API TEST



# 1. pjt08

## 명령어

```bash
$ python manage.py djangorestframework

$ python manage.py loaddata movies/actors.json movies/movies.json movies/reviews.json
```



## `views.py`

* POST 할 때, `ReviewSerializer(review, request.data)` request.data를 인자로 받는 이유
* {review_pk}로 반환해주는 이유

```python
@api_view(['GET', 'PUT', 'DELETE'])
def review_detail(request, review_pk):
    review = get_object_or_404(Review, pk=review_pk)
    if request.method == 'GET':
        serializer = ReviewSerializer(review)
        return Response(serializer.data)
    elif request.method == 'PUT':
        serializer = ReviewSerializer(review, request.data)
        if serializer.is_valid(raise_exception=True):
            serializer.save()
            return Response(serializer.data)
    elif request.method == 'DELETE':
        review.delete()
        data = {
            'data': f'review {review_pk} is deleted',
        }
        return Response(data, status=status.HTTP_204_NO_CONTENT)
```

* serializer.save()의 인자로 movie=movie 를 받는 이유
* request.data를 MovieSerializer의 인자로 받는 이유

```python
@api_view(['POST'])
def create_review(request, movie_pk):
    movie = get_object_or_404(Movie, pk=movie_pk)
    serializer = MovieSerializer(movie, request.data)
    if serializer.is_valid(raise_exception=True):
        serializer.save(movie=movie)
        return Response(serializer.data, status=status.HTTP_201_CREATED)
```

* serializer에 Review serializer인거

```python
@api_view(['POST'])
def create_review(request, movie_pk):
    movie = get_object_or_404(Movie, pk=movie_pk)
    serializer = ReviewSerializer(movie, request.data)
    if serializer.is_valid(raise_exception=True):
        serializer.save(movie=movie)
        return Response(serializer.data, status=status.HTTP_201_CREATED)
```





## `serializers.py`

* 역참조 할 때 인스턴스 + read_only 이유

```python
class ActorSerializer(serializers.ModelSerializer):
    movie_set = MovieTitleSerializer(many=True, read_only=True)

    class Meta:
        model = Actor
        fields = '__all__'
```



## `models.py`

* ManyToManyField 인자

```python
class Movie(models.Model):
    title = models.CharField(max_length=100)
    overview = models.TextField()
    release_date = models.DateTimeField()
    poster_path = models.TextField()
    actors = models.ManyToManyField(Actor)
```

* Foreign Key가 받는 인자(왜 Movie인지)

```python
class Review(models.Model):
    title = models.CharField(max_length=100)
    content = models.TextField()
    movie = models.ForeignKey(Movie, on_delete=models.CASCADE)
```



# 2. hws1

## 1. 명령어

```bash
$ pip install django-seed

$ python manage.py makemigrations
$ python manage.py migrate

$ python manage.py seed [app_name] --number=[num]
```



## 2. `views.py`

* POST일 때, data=request.data 가 ArticleSerializer의 인자로 받아짐

```python
@api_view(['GET', 'POST'])
def article_list(request):
    articles = get_list_or_404(Article)
    if request.method == 'GET':
        serializer = ArticleListSerializer(articles, many=True)
        return Response(serializer.data)
    elif request.method == 'POST':
        serializer = ArticleSerializer(data=request.data)
        if serializer.is_valid(raise_exception=True):
            serializer.save()
            return Response(serializer.data)
```

* PUT일 때, ArticleSerializer에 article, request.data가 둘 다 인자로 받아짐
* DELETE일 때, Response() 안에 인자로 data만 받아오기

```python
@api_view(['GET', 'PUT', 'DELETE'])
def article_detail(request, article_pk):
    article = get_object_or_404(Article, pk=article_pk)
    if request.method == 'GET':
        serializer = ArticleSerializer(article)
        return Response(serializer.data)
    elif request.method == 'PUT': 
        serializer = ArticleSerializer(article, request.data)
        if serializer.is_valid(raise_exception=True):
            serializer.save()
            return Response(serializer.data)
    elif request.method == 'DELETE':
        serializer = ArticleSerializer(article)
        article.delete()
        data = {
            'data': {article_pk}
        }
        return Response(data)
```





# 3. hws2

* `urls.py`에서 오타 조심하기! 특히 괄호 닫고 안닫고 확인



## 1. `views.py`

* POST(생성)일때는, ArtistSerializer(data=request.data)
* save()의 인자로 artist=artist 받아주는 것

```python
@api_view(['GET', 'POST'])
def artist_list(request):
    artists = get_list_or_404(Artist)
    if request.method == 'GET':
        serializer = ArtistListSerializer(artists, many=True)
        return Response(serializer.data)
    elif request.method == 'POST':
        serializer = ArtistSerializer(data=request.data)
        if serializer.is_valid(raise_exception=True):
            serializer.save()
            return Response(serializer.data, status=status.HTTP_201_CREATED)

@api_view(['POST'])
def create_music(request, artist_pk):
    artist = get_object_or_404(Artist, artist_pk)
    serializer = ArtistSerializer(data=request.data)
    if serializer.is_valid(raise_exception=True):
        serializer.save(artist=artist)
        return Response(serializer.data, status=status.HTTP_201_CREATED)

```



