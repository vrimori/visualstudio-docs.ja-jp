---
title: "その他の Visual Studio のエディションでモデルおよびダイアグラムを読み取る |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: models, versions of Visual Studio
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1483fe7d62baf5d81865897308fb9d25947213c3
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Visual Studio の他のエディションでモデルおよびダイアグラムを読み取る
モデルの作成をサポートしていないバージョンの Visual Studio でモデルを開くと、モデルは読み取り専用モードで開きます。 このモードでは、ダイアグラムのレイアウトは変更できますが、モデルは変更できません。  
  
 モデルの作成をサポートする Visual Studio のバージョンを参照してください[アーキテクチャおよびモデリング ツールのバージョン サポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)です。  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>モデルおよび図へのアクセス  
 依存関係ダイアグラムを読み取りするにはまず Visual Studio を使用して、モデリング プロジェクトを開くし、内にダイアグラムを開きます。  
  
 このため、依存関係ダイアグラムを読みたい場合もが必要が作成されたモデリング プロジェクトへのアクセスです。 これを行うには、[!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] からプロジェクトにアクセスするか、プロジェクト ファイルのコピーを取得します。  
  
> [!NOTE]
>  これは、コードから生成されたコード マップおよび .NET クラス図には適用されません。 これらの図はモデリング プロジェクトとは関係なく表示できます。  
  
 依存関係ダイアグラムを読み取り、必要なファイルの最小セットのとおりです。  
  
-   読みたい、たとえば、ダイアグラムのファイルの図は、2 つ**MyDiagram.classdiagram と MyDiagram.classdiagram.layout**です。  
  
    > [!NOTE]
    >  依存関係図もが必要という名前のファイル * MyDiagram ***. layerdiagram.suppressions**です。  
  
-   モデリング プロジェクト ファイル (**MyModel.modelproj**)  
  
-   ルート モデル ファイル (**ModelDefinition\MyModel.uml**)  
  
-   ダイアグラムで参照されているいずれかのパッケージ用のパッケージ ファイル (**ModelDefinition\MyPackage.uml**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>読み取り専用モードで行える変更  
 モデルの作成をサポートしていないバージョンの Visual Studio でモデルおよびその図を開く場合、モデルは変更できません。 つまり、図またはモデル エクスプローラーに表示されている要素と関係は変更できません。 ただし、図のレイアウトに次のような変更を加えることはできます:  
  
-   図形およびコネクタを図に再配置する。  
  
-   図形を展開および折りたたむ。  
  
 これらの変更は保存できます。 変更内容を他のユーザーに表示されるようにする場合は、する必要がありますには、少なくとも送信する、更新された**.layout**ファイル。  
  
##  <a name="RelatedTopics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[依存関係図: リファレンス](../modeling/layer-diagrams-reference.md)|レイヤー図には、既存のアーキテクチャまたは提案されるアーキテクチャの構造が示されます。 コードを記述する際に、レイヤー図と照らし合わせて自動的に検証されるようにできます。|  
  
## <a name="see-also"></a>参照  
 [アプリのモデルを生成する](../modeling/create-models-for-your-app.md)