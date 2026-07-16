# Unity Portfolio Project Tables

유니티 포트폴리오 프로젝트에서 사용하는 데이터 테이블 저장소입니다.
메인 클라이언트 프로젝트가 아니라, 게임 데이터 원본과 변환 도구를 따로 관리하기 위한 보조 저장소입니다.

게임 데이터는 Excel 테이블로 작성하고, `TableDataConverter.exe`를 통해 Unity 프로젝트에서 사용할 데이터 파일과 코드로 변환합니다.

## Project Role

이 저장소는 아래 역할을 담당합니다.

- 게임 데이터 원본 Excel 테이블 관리
- 테이블 번호와 이름 규칙 관리
- Unity 클라이언트에서 사용할 데이터 산출물 생성
- 아이템, 캐릭터, 장비, 미션, 텍스트 데이터 분리 관리

전체 게임 클라이언트 구현, 씬, 프리팹, UI, 런타임 코드는 이 저장소의 범위에 포함하지 않습니다.

## Repository Contents

- `_<TableNo>_<Name>.xlsx`: 원본 데이터 테이블
- `TableDataConverter.exe`: 테이블 변환 실행 파일
- `README.md`: 테이블 관리 규칙과 사용 안내

## Data Flow

```text
Excel Table
    -> TableDataConverter.exe
        -> Data byte files
        -> Table classes
        -> Table Data Loader
            -> Unity client
```

원본 데이터는 Excel 파일을 기준으로 관리하고, Unity에서 직접 사용하는 파일은 컨버터 결과물로 갱신합니다.

## Table List

| File | Description |
| --- | --- |
| `_000_Global_Define.xlsx` | 전역 정의 및 공통 상수 데이터 |
| `_101_Items.xlsx` | 아이템 기본 데이터 |
| `_102_Character.xlsx` | 캐릭터 기본 데이터 |
| `_104_Missions.xlsx` | 미션 데이터 |
| `_105_Armors.xlsx` | 방어구 데이터 |
| `_106_Weapons.xlsx` | 무기 데이터 |
| `_800_Notice.xlsx` | 공지 데이터 |
| `_900_TextCommon.xlsx` | 공통 텍스트 데이터 |
| `_901_TextCharacter.xlsx` | 캐릭터 관련 텍스트 데이터 |
| `_902_TextNotice.xlsx` | 공지 관련 텍스트 데이터 |
| `_903_TextMissions.xlsx` | 미션 관련 텍스트 데이터 |
| `_904_TextItems.xlsx` | 아이템 관련 텍스트 데이터 |

## Table Naming

테이블 파일은 아래 형식을 따릅니다.

```text
_<TableNo>_<TableName>.xlsx
```

예시:

- `_000_Global_Define.xlsx`
- `_101_Items.xlsx`
- `_102_Character.xlsx`
- `_900_TextCommon.xlsx`

`TableNo`는 변환 결과물의 클래스명과 데이터명 접두사로 사용됩니다.

## Converter Output

컨버터 실행 시 Unity 프로젝트에서 사용하는 산출물이 자동 생성됩니다.

- 데이터 byte 파일
- 테이블 클래스
- Table Data Loader

생성된 파일은 컨버터 결과물이므로 직접 수정하지 않습니다.

## Portfolio Focus

이 저장소에서는 아래 내용을 중점적으로 보여줍니다.

- Excel 기반 게임 데이터 관리 구조
- 테이블 번호를 기준으로 한 데이터/클래스 네이밍 규칙
- 원본 데이터와 Unity 사용 데이터를 분리하는 방식
- 아이템, 장비, 캐릭터, 미션, 텍스트 테이블의 역할 분리
- 컨버터를 통한 반복 작업 자동화

## Edit Rules

- Excel 테이블을 수정한 뒤 컨버터를 실행해 결과물을 갱신합니다.
- `TableLoader`와 테이블 번호 접두사가 붙은 클래스 및 데이터 파일은 직접 수정하지 않습니다.
- 변환 결과에 문제가 있으면 생성 파일을 고치지 말고 컨버터 또는 원본 테이블을 수정합니다.
- 컨버터 관련 변경은 별도 프로젝트에서 관리합니다.

## Notes

- 이 저장소는 데이터 테이블 관리용 저장소입니다.
- 실제 게임 실행 화면과 클라이언트 구현은 별도 Unity 프로젝트에서 관리합니다.
- 테이블 구조가 바뀌면 컨버터와 Unity 쪽 로딩 코드의 호환성을 함께 확인해야 합니다.

## Converter Project

컨버터 소스와 업데이트는 아래 저장소에서 관리합니다.

[TableDataConverter](https://github.com/GyoolTomato/TableDataConverter)

## Changelog

### v0.1

- 버전 네이밍 추가
