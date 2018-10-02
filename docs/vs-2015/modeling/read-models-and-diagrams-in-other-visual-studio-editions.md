---
title: その他の Visual Studio のエディションでモデルおよびダイアグラムを読み取る |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 22
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: a4642086639fad8a5b39e4a03d4509b349807a9b
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592887"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Visual Studio の他のエディションでモデルおよびダイアグラムを読み取る
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[他の Visual Studio のエディションでモデルおよびダイアグラムを読み取る](https://docs.microsoft.com/visualstudio/modeling/read-models-and-diagrams-in-other-visual-studio-editions)します。  
  
モデルの作成をサポートしていないバージョンの Visual Studio でモデルを開くと、モデルは読み取り専用モードで開きます。 このモードでは、ダイアグラムのレイアウトは変更できますが、モデルは変更できません。  
  
 モデルの作成をサポートする Visual Studio のバージョンを確認するを参照してください。[アーキテクチャとモデリング ツールのバージョンのサポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)します。  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>モデルおよび図へのアクセス  
 UML 図またはレイヤー図を読み取るには、まず Visual Studio を使用して、モデリング プロジェクトを開き、し、その中で図を開く必要があります。  
  
 このため、UML 図またはレイヤー図を読み取る場合は、その図を生成したモデリング プロジェクトにアクセスできる必要があります。 これを行うには、[!INCLUDE[esprscc](../includes/esprscc-md.md)] からプロジェクトにアクセスするか、プロジェクト ファイルのコピーを取得します。  
  
> [!NOTE]
>  これは、コードから生成されたコード マップおよび .NET クラス図には適用されません。 これらの図はモデリング プロジェクトとは関係なく表示できます。  
  
 UML 図またはレイヤー図を読み取るのに必要なファイルの最小セットは次のとおりです。  
  
-   2 つのダイアグラム ファイルを読み取るには、たとえば、ダイアグラムの**MyDiagram.classdiagram と MyDiagram.classdiagram.layout**します。  
  
    > [!NOTE]
    >  レイヤー図もが必要という名前のファイル_MyDiagram_**. layerdiagram.suppressions**します。  
  
-   モデリング プロジェクト ファイル (**MyModel.modelproj**)  
  
-   ルート モデル ファイル (**ModelDefinition\MyModel.uml**)  
  
-   ダイアグラムで参照されているすべてのパッケージのパッケージ ファイル (**ModelDefinition\MyPackage.uml**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>読み取り専用モードで行える変更  
 モデルの作成をサポートしていないバージョンの Visual Studio でモデルおよびその図を開く場合、モデルは変更できません。 つまり、図またはモデル エクスプローラーに表示されている要素と関係は変更できません。 ただし、図のレイアウトに次のような変更を加えることはできます:  
  
-   図形およびコネクタを図に再配置する。  
  
-   図形を展開および折りたたむ。  
  
 これらの変更は保存できます。 変更内容を他のユーザーに表示されるようにする場合は、送信しなければならない以上で、更新された **.layout**ファイル。  
  
##  <a name="RelatedTopics"></a> 関連トピック  
  
|Title|説明|  
|-----------|-----------------|  
|[レイヤー図: リファレンス](../modeling/layer-diagrams-reference.md)|レイヤー図には、既存のアーキテクチャまたは提案されるアーキテクチャの構造が示されます。 コードを記述する際に、レイヤー図と照らし合わせて自動的に検証されるようにできます。|  
|[UML アクティビティ図: リファレンス](../modeling/uml-activity-diagrams-reference.md)|アクティビティ図には、業務処理またはソフトウェアのワーク フローが示されます。|  
|[UML クラス図: リファレンス](../modeling/uml-class-diagrams-reference.md)|クラス図には、コード、データベース スキーマ、通信プロトコルなど、さまざまなコンテキストで使用される型および関係、またはビジネス ドメインの説明に使用される用語集が示されます。|  
|[UML コンポーネント図: リファレンス](../modeling/uml-component-diagrams-reference.md)|コンポーネント図には、ソフトウェア設計で他のパートから分離可能なパートと、それらのインターフェイスが示されます。|  
|[UML シーケンス図: リファレンス](../modeling/uml-sequence-diagrams-reference.md)|シーケンス図には、ソフトウェア設計での要素間の相互作用が示されます。|  
|[UML ユース ケース図: リファレンス](../modeling/uml-use-case-diagrams-reference.md)|ユース ケース図には、システムのユーザーと、特定の目的を達成するためにユーザーが実行できるアクティビティが示されます。|  
  
## <a name="see-also"></a>関連項目  
 [アプリのモデルを生成する](../modeling/create-models-for-your-app.md)



