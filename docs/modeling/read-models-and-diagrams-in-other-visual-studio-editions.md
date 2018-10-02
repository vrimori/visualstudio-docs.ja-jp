---
title: Visual Studio の他のエディションでモデルおよびダイアグラムを読み取る
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: cfd6188bc4d48f26e85ae8778d75d2fa99ef0f25
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859680"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Visual Studio の他のエディションでモデルおよびダイアグラムを読み取る
モデルの作成をサポートしていないバージョンの Visual Studio でモデルを開くと、モデルは読み取り専用モードで開きます。 このモードでは、ダイアグラムのレイアウトは変更できますが、モデルは変更できません。

 モデルの作成をサポートする Visual Studio のバージョンを確認するを参照してください。[アーキテクチャとモデリング ツールのバージョンのサポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)します。

## <a name="obtaining-access-to-a-model-and-diagrams"></a>モデルおよび図へのアクセス
 依存関係図を読み取るには、まず Visual Studio を使用して、モデリング プロジェクトを開き、し、その中で図を開く必要があります。

 このため、依存関係図を読みたい場合も必要が作成されたモデリング プロジェクトへのアクセス。 これを行うか、ソース管理からプロジェクトにアクセスするか、プロジェクト ファイルのコピーを取得します。

> [!NOTE]
>  これは、コードから生成されたコード マップおよび .NET クラス図には適用されません。 これらの図はモデリング プロジェクトとは関係なく表示できます。

 依存関係図を読み取るには、必要なファイルの最小セットがとおりです。

-   2 つのダイアグラム ファイルを読み取るには、たとえば、ダイアグラムの**MyDiagram.classdiagram と MyDiagram.classdiagram.layout**します。

    > [!NOTE]
    >  依存関係を示す図については、という名前のファイルもがする必要があります_MyDiagram_**. layerdiagram.suppressions**します。

-   モデリング プロジェクト ファイル (**MyModel.modelproj**)

-   ルート モデル ファイル (**ModelDefinition\MyModel.uml**)

-   ダイアグラムで参照されているすべてのパッケージのパッケージ ファイル (**ModelDefinition\MyPackage.uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>読み取り専用モードで行える変更
 モデルの作成をサポートしていないバージョンの Visual Studio でモデルおよびその図を開く場合、モデルは変更できません。 つまり、図またはモデル エクスプローラーに表示されている要素と関係は変更できません。 ただし、図のレイアウトに次のような変更を加えることはできます:

-   図形およびコネクタを図に再配置する。

-   図形を展開および折りたたむ。

 これらの変更は保存できます。 変更内容を他のユーザーに表示されるようにする場合は、送信しなければならない以上で、更新された **.layout**ファイル。

## <a name="RelatedTopics"></a> 関連トピック

|Title|説明|
|-----------|-----------------|
|[依存関係図: リファレンス](../modeling/layer-diagrams-reference.md)|レイヤー図には、既存のアーキテクチャまたは提案されるアーキテクチャの構造が示されます。 コードを記述する際に、レイヤー図と照らし合わせて自動的に検証されるようにできます。|

## <a name="see-also"></a>関連項目

- [アプリのモデルを生成する](../modeling/create-models-for-your-app.md)