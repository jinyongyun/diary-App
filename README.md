# diary-App
하루하루 인생기록 일기장 앱

## 활용 기술
UITabBarController
UICollectionView
NotificationCenter

## UITabBarController

UITabBar
앱에서 서로 다른 하위작업, 뷰, 모드 사이의 선택을 할 수 있도록
탭바에 하나 혹은 하나 이상의 버튼을 보여주는 컨트롤

UITabBarController
다중 선택 인터페이스를 관리하는 컨테이너 뷰 컨트롤러로 선택에 따라 어떤 자식 뷰 컨트롤러를 보여줄지 결정

## UICollectionView
데이터 항목의 정렬된 컬렉션을 관리하고 커스텀한 레이아웃을 이용해 표시하는 객체 
컬렉션 뷰는 supplementary View와 cell로 구현되는데
cell은 컬렉션 뷰의 콘텐츠를 표시하고
Supplymentary View는 섹션에 대한 정보를 표시한다
그리고 Decoratoin View는 컬렉션 뷰의 배경을 꾸밀 때 사용하는 뷰이다.
컬렉션 뷰는 레이아웃 객체를 이용해 컬렉션 뷰 내부 아이템을 배치 및 시각적 스타일을 결정한다.
레이아웃 객체가 하는 일은 cell, supplymentary view 그리고 collection view의 bound, 내부에 있는 decoration view의 위치를 결정하고
시각적 상태의 정보를 UICollectionView에 제공한다.
UICollectionView에서는 UIFlowLayout 클래스의 레이아웃 객체를 사용해서 항목들을 정렬할 수 있다
해당 클래스를 사용하게 되면 셀을 원하는 형태로 정렬할 수 있다
flowlayout은 행의 선형 경로를 정렬한다.

# FlowLayout의 구성단계
1.flow layout 객체를 작성하고 컬렉션 뷰에 할당한다
2. 셀의 width, height을 정한다 ( 반드시 지정 이거 안하면 표시 안 됨)
3. 필요한 경우 셀들 간의 좌우 간격, 위아래 최소 간격을 설정한다 ( 셀들의 크기가 다를 경우 실제로 나타난 최소 간격이 다를 수 있다)
4. 섹션에 header와 footer가 있다면 이들의 크기를 정한다
5. 레이아웃의 스크롤 방향을 설정한다

셀과 셀 사이의 간격 뿐만 아니라, 섹션 자체의 공간을 줄 수 있다.
Top, Left, Right, Bottom을 지정할 수 있고
inset = UIEdgeInsetsMake(top, left, bottom, right)을 이용한다.

## UICollectionViewDataSource
컬렉션 뷰는 이전에 배운 테이블 뷰와 마찬가지로 데이터 소스에 따라 사용자에게 어떤 컨텐츠를 보여줄지 표시한다
UICollectionViewDataSource는 컬렉션 뷰로 보여주는 콘텐츠들을 관리하는 객체이다.
데이터 소스를 정의하기 위해서는 UICollectionViewDataSource 프로토콜을 준수해야하고
DataSource의 역할은 CollectionView에 몇 개의 섹션이 있는지, 특정 섹션에 몇 개의 셀이 있는지, 특정 섹션이나 셀의 컨텐츠를 보여주기 위해 어떤 뷰를 사용할 것인지 같은 정보를 컬렉션 뷰에 제공하는 역할을 한다.

public protocol UICollectionViewDataSource : NSObjectProtocol {
//지정한 셀에 표시할 셀의 개수를 묻는 메소드 필수 구현
  func collectionView(_ collectionView: UICollectionView, numberOfItemsInSection section: Int) -> Int
//컬렉션 뷰의 지정된 위치에 표시할 셀을 요청하는 메소드 필수 구현
 func collectionView(_ collectionView: UICollectionView, CellForItemAt indexPath: IndexPath) -> UICollectionViewCell

 }
 
 ## UICollectionViewDelegate
 콘텐의 표현, 사용자와의 상호작용과 관련된 것들을 관리하는 객체, dataSource와 다르게 delegate는 필수로 구현하지 않아도 된다.
 
