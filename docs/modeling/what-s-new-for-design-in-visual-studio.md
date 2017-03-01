---
title: "Visual Studio での設計の新機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 32
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 17bc5792d4fa9fac0b97705e61372dcc884c82a2
ms.openlocfilehash: 2704914ab8607e0a7442a45589e6a6cab08b7338
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-for-design-in-visual-studio"></a>Visual Studio での設計の新機能します。

## <a name="live-dependency-validation"></a>ライブの依存関係の検証

技術的な負債を管理する重要な部分は、不要な依存関係を削除します。
依存関係のライブの検証が含まれるの問題に関する正確な情報を提供して、エラーの一覧と、エディターの新機能から完全に利用します。

![ライブの依存関係の検証の動作](media/dep-validation-whatsnew-01.png)

編集の動作は、「レイヤー図」から「依存関係図」の用語を変更するよりデータを検出しやすく、依存関係の検証を行うに変更されました。

**アーキテクチャ**メニューが直接依存関係のダイアグラムを作成するコマンドを含むようになりました。

![[アーキテクチャ] メニュー項目をライブの依存関係](media/dep-validation-whatsnew-02.png)

... わかりやすいように、依存関係のダイアグラムでは、およびその説明、レイヤーのプロパティの名前が変更されているとします。

![ライブの依存関係プロパティの名前を更新します。](media/dep-validation-whatsnew-03.png)

表示されるよう、ソリューション内の現在のコードの分析結果にすぐに、変更の影響、ダイアグラムを保存するたびに。 できなくなります「依存関係の検証」コマンドが完了するを待機する必要はありません。

詳細については、次を参照してください。[このブログの投稿](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/)します。 
 
## <a name="uml-designers-have-been-removed"></a>UML デザイナー向けが削除されました

UML デザイナーは、このバージョンの Visual Studio Enterprise から削除されました。

* UML 図が XML ファイルとして表示されるようになりました
* UML モデル エクスプ ローラーが存在しません
* モデリング プロジェクトの参照は依存関係の検証は使用しません
* ソリューション エクスプ ローラーで、[レイヤー参照設定] ノードは表示されなくなります
* 依存関係 (層) の図に、「検証」ビルド アクションは使用されなく - ビルド タスクが削除されました 
* プロジェクトの構造は、バージョン間のラウンド トリップの維持します。
* ことができますまだを開く、作成、編集、および (層) の依存関係図を XML として保存
* 依存関係 (層) の図にリンクされている TFS の作業項目は、デザイン画面にアクセスできません。
* DSL またはレイヤーから後方リンクはサポートされていません 
* Modeling SDK で UML 拡張機能はサポートされていません

ただし、使用は .NET と C++ コードのアーキテクチャを視覚化するサポート[コード マップの](map-dependencies-across-your-solutions.md)、および上記で説明した依存関係の検証を大幅に向上します。

UML デザイナー向けの重要なユーザーの場合は、UML のニーズに代替のツールを決定するときに、Visual Studio 2015 または以前のバージョンを使用する続行することができます。

詳細については、次を参照してください。[このブログの投稿](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)します。 

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

<a name="VersionSupport"></a>
##  <a name="version-support-for-architecture-and-modeling-tools"></a>アーキテクチャ ツールとモデリング ツールのバージョン サポート  

Visual Studio には、使用できるバージョンがいくつかあります。 そのうちの一部においては、アーキテクチャ ツールとモデリング ツールのサポートが提供されていません。 各ツールの利用可能情報を次の表に示します。  
  
|**機能**|**Enterprise**|**Professional**|**Community**|**Express**|  
|-----------------|--------------------|----------------------|-------------------|-----------------|  
|**コード マップ**|はい|注 (1) を参照してください。|-|-|  
|**依存関係図**|はい|注 (2) を参照してください。|注 (2) を参照してください。|-|  
|**グラフを向け**(DGML ダイアグラム)|はい|はい|はい|-|  
|**コード クローン**|はい|-|-|-|  
  
注 (1): コード マップの読み取り、コード マップのフィルター処理、新しいジェネリック ノードの追加、選択範囲からの新しい有向グラフの作成のみをサポートします。

注 (2): 依存関係図の解説をのみサポートします。

