We all know this, but it is worth reminding it sometimes...

```C++

  static void BM_Push(benchmark::State& state) 
  {
    while (state.KeepRunning())
    {
      std::vector<int> vect;
      for (int i=0; i<100; i++) vect.push_back(i) ;
    }
  }
  // Register the function as a benchmark
  BENCHMARK(BM_Push);

  static void BM_Reserve(benchmark::State& state) 
  {
    while (state.KeepRunning())
    {
      std::vector<int> vect;
      vect.reserve(100);
      for (int i=0; i<100; i++) vect.push_back(i);
    }
  }
  BENCHMARK(BM_Reserve);

  static void BM_Resize(benchmark::State& state) 
  {
    while (state.KeepRunning())
    {
      std::vector<int> vect;
      vect.resize(100);
      for (int i=0; i<100; i++) vect[i] = (i) ;
    }
  }

  BENCHMARK(BM_Resize);
```
