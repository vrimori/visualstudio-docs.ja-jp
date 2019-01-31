---
title: IntelliTest の概要
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Get started
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: fb7fc6049bd916c766651484da0c53b3aeccbe35
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929370"
---
# <a name="get-started-with-microsoft-intellitest"></a>Microsoft IntelliTest の概要

* IntelliTest を初めて使用する場合
  * [Channel 9 ビデオ](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)を見る
  * この [MSDN マガジンに記載されている概要](https://msdn.microsoft.com/magazine/dn904672.aspx)を読む
  * Microsoft の[ドキュメント](../../test/generate-unit-tests-for-your-code-with-intellitest.md)を読む
* [Stack Overflow](http://stackoverflow.com/questions/tagged/intellitest) で質問する
* このリファレンス マニュアルの残りの部分を読む
* クイック リファレンスのこのページを印刷する

## <a name="important-attributes"></a>重要な属性

* [PexClass](attribute-glossary.md#pexclass): **PUT** を含む型をマークします。
* [PexMethod](attribute-glossary.md#pexmethod): **PUT** をマークします。
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull): null 以外のパラメーターをマークします。

```csharp
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest): テスト プロジェクトをプロジェクトにバインドします。
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute): インストルメント化するアセンブリを指定します。

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="helper-classes"></a> 重要な静的ヘルパー クラス

* [PexAssume](static-helper-classes.md#pexassume): 前提事項 (入力フィルター) を評価します。
* [PexAssert](static-helper-classes.md#pexassert): アサーションを評価します。
* [PexChoose](static-helper-classes.md#pexchoose): 新しい選択項目 (追加入力) を生成します。
* [PexObserve](static-helper-classes.md#pexobserve): ライブ値を生成されたテストに記録します。

```csharp
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="got-feedback"></a>フィードバックをお寄せください

ご意見や機能に関するご要望を[開発者コミュニティ](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)で投稿してください。
