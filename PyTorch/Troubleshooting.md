# Troubleshooting

## OOM(Out Of Memory)
- 어디서, 왜 발생했는지 알기 어렵고, Error backtracking 도 어렵다.
- 가장 단순한 해결법은 Batch Size 를 줄이고 GPU clean 을 한 다음에 다시 돌려보는 것이다.

### 해결법
#### GPUtil 사용하기
```python
!pip install GPUtil

import GPUtil
GPUtil.showUtilization()
```
- GPU 를 상태를 보여주기 때문에 편하다.

#### torch.cuda.empty_cache()
- 사용되지 않는 GPU cache 를 정리해 가용 메모리를 확보하는 방법
#### trainning loop 에 tensor 로 축적되는 변수 확인하기
- Tensor 로 처리된 변수는 GPU 메모리를 사용하기 때문에 loop 안에 있으면 계속 메모리에 쌓이면서 메모리를 잡아먹는다.
	- 1-d tensor 의 경우 python 기본 객체로 변환해 사용한다.
	- del 명령어를 사용해 필요 없어진 변수는 삭제해준다.
#### 가능한 batch size 실험해보기

#### torch.no_grad() 사용하기
- backward 가 일어나지 않기 때문에 메모리를 추가적으로 사용하지 않는다.

