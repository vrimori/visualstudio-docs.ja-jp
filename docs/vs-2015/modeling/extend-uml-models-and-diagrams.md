---
title: UML モデルと図の拡張 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: b5bfa61e-ea59-4c3b-b5af-53475d7d13cd
caps.latest.revision: 39
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: d15da471e077e737bb7ba82d19d68f24f15db687
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533537"
---
# <a name="extend-uml-models-and-diagrams"></a>UML モデルと図の拡張
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[UML を拡張モデルと図](https://docs.microsoft.com/visualstudio/modeling/extend-uml-models-and-diagrams)します。  
  
ここでは、Visual Studio に含まれている UML モデリング ツールを拡張するためのいくつかの方法について説明します。 モデルの型とツールをサポートする Visual Studio のバージョンを確認するを参照してください。[アーキテクチャとモデリング ツールのバージョンのサポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)します。  
  
 次の例のシナリオでは、Fabrikam 社は空港の荷物取り扱いシステムを設計し、インストールします。 ある空港のプロジェクトと別の空港のプロジェクトの間には、基本的な設備とそれを制御するソフトウェアに関して多くの類似点があります。 ただし、コンベヤ ベルト、チェックイン デスク、保管庫、その他の荷物取り扱い装置の構成など、大きく異なる点もいくつかあります。  
  
 新しいプロジェクトを開始するにあたり、Fabrikam 社のチームは、チーム内および顧客との間でこれらの要件についての議論を円滑にするために UML モデルを作成します。 このチームは、アクティビティ図を使用して荷物の流れを表すことにしました。この図において、オブジェクト ノードは各設備を表します。 この UML モデルは、システムのコードを直接表すわけではありません。  
  
 Fabrikam 社のツール チームは、一連の拡張機能を作成して開発チームを支援します。 以降のセクションでは、定義可能なさまざまな拡張機能について説明します。 これらの手法のいくつかを 1 つの Visual Studio 拡張機能に結合できます。  
  
 詳細については、このビデオをご覧ください:![ビデオへのリンク](../data-tools/media/playvideo.gif "PlayVideo")[MSDN How Do I シリーズ: UML ツールと機能拡張](http://go.microsoft.com/fwlink/?LinkId=214467)します。  
  
##  <a name="Requirements"></a> 要件  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
-   [Modeling SDK for Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=48148)。  
  
## <a name="profiles"></a>プロファイル  
 プロファイルを使用すると、UML 要素のステレオタイプと追加のプロパティを定義できます。  
  
 Fabrikam 社のツール開発者は、アクティビティ図のオブジェクト ノードにステレオタイプ (たとえば、«コンベヤ ベルト»、«チェックイン デスク») を定義します。 チーム メンバーがアクティビティ図を使用して荷物取り扱いスキームを作成すると、ツール開発者はステレオタイプを設定して各ノードが表す設備の種類を示すことができるようになります。 ツール開発者は、いくつかのステレオタイプに対して追加のプロパティを定義して、ユーザーがコンベヤ ベルトの容量やチェックイン デスクの左右の区別などの値を記録できるようにします。  
  
 詳細については、次を参照してください。 [UML を拡張するプロファイルを定義して](../modeling/define-a-profile-to-extend-uml.md)します。  
  
## <a name="custom-toolbox-items"></a>カスタム ツールボックス項目  
 カスタム ツールボックス項目は、図で定義するプロトタイプから要素や要素グループを作成します。 たとえば、特定の色またはステレオタイプのユース ケースを作成するツールや、設計パターンを表すクラスと関連のグループを作成することもできます。 これらのツールボックス項目を Visual Studio 拡張機能に追加し、他のユーザーに配布できます。  
  
 詳細については、次を参照してください。[定義のカスタム モデリング ツールボックス アイテム](../modeling/define-a-custom-modeling-toolbox-item.md)します。  
  
## <a name="validation"></a>検証  
 UML モデルが指定の制約に確実に準拠するようにするための規則を定義できます。  
  
 Fabrikam 社のツール開発者は、荷物取り扱いモデルでチーム メンバーが単純なミスを犯すことがないように規則を定義します。 たとえば、チェックイン デスクを保管庫に直接接続することはできません。 これらの間には、少なくともベルト コンベヤが存在する必要があります。  
  
 詳細については、次を参照してください。 [UML モデルの検証制約を定義](../modeling/define-validation-constraints-for-uml-models.md)します。  
  
## <a name="menu-commands"></a>メニュー コマンド  
 UML 図内の要素をユーザーが右クリックすることで呼び出せるコマンドを定義できます。 これらのコマンドを使用して、モデルおよび図を更新したり、[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] でその他の操作を実行したりできます。  
  
 Fabrikam 社では、"チェックイン デスクを作成した後で選択したベルト コンベヤに接続する"、"会社のレイアウト規則に従って図を配置し直す" などのよく実行される操作を自動化するためのメニュー コマンドを定義します。  
  
 参照してください[モデリング図にメニュー コマンドを定義](../modeling/define-a-menu-command-on-a-modeling-diagram.md)します。  
  
## <a name="gestures"></a>ジェスチャ  
 ユーザーが図の要素をダブルクリックするか、要素を図や図内の要素にドラッグすることで起動されるコマンドを定義できます。 他の UML 図、Visual Studio の他の部分、または他のアプリケーションや Windows エクスプローラー (またはエクスプローラー) からドラッグされた項目を処理できるコマンドを定義できます。  
  
 Fabrikam 社のチーム メンバーは、仕様などのファイルを、Windows デスクトップからドラッグすることで、任意のモデル要素に関連付けることができます。 ツール開発者は、任意の要素にファイル パス プロパティを提供するステレオタイプと、ファイルが要素上にドロップされたときにステレオタイプとファイル パスを設定するジェスチャを定義しました。  
  
 詳細については、次を参照してください。[モデリング図にジェスチャ ハンドラーを定義](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)します。  
  
## <a name="responding-to-changes"></a>変更への対応  
 モデル内の変更が、ユーザー アクションに起因するものか、他のプログラム コードに起因するものかにかかわらず、変更に対応するコードを作成できます。  
  
 Fabrikam 社の開発者は、要素の色をそのステレオタイプに応じて自動的に設定するコードを作成します。 これにより、ユーザーはモデル内の要素のそれぞれ異なる役割を簡単に区別できるようになります。  
  
 詳細については、次を参照してください。[方法: UML モデルの変更に応答](../misc/how-to-respond-to-changes-in-a-uml-model.md)します。  
  
## <a name="model-bus"></a>モデル バス  
 モデル バスを使用すると、別の図または別の [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 拡張機能から図またはモデルにアクセスできます。 特に、複数のモデルに情報を伝達することができるため、結合されたモデルで複数の人が同時に作業できます。  
  
 Fabrikam 社では、アクティビティ図上の要素を使用して、荷物取り扱い設備を表します。 設備の各項目については、別の図で詳細な仕様を記述できます。この図は、別のモデルに配置することもできます。 荷物フロー図の検証制約では、他の図から設備の関連プロパティを取得できます。 他の図への参照は、ステレオタイプに定義された追加のプロパティに格納されます。  
  
 詳細については、次を参照してください。[を他のモデルおよびツールとの統合の UML モデル](../modeling/integrate-uml-models-with-other-models-and-tools.md)します。  
  
## <a name="generation"></a>生成  
 1 つのモデルから、プログラム コード、スクリプト、構成、ドキュメント、新しいモデル、またはその他の成果物を生成できます。  
  
 Fabrikam 社が設計する荷物取り扱いシステムのプログラム コードの多くは、複数のプロジェクトで共通しています。 主な変動要素は、空港における荷物の流れです。 設計チームが初期のいくつかのプロジェクトを経験した後、ツール開発者は、荷物フロー モデルから可変のプログラム コードの大部分およびその他のファイル (ユーザー ドキュメントなど) を生成するテンプレートを作成します。 これにより、新しいプロジェクトの開発時間が大幅に短縮され、エラー発生率も引き下げられます。  
  
 詳細については、次を参照してください。 [UML モデルからファイルを生成](../modeling/generate-files-from-a-uml-model.md)します。  
  
## <a name="team-foundation-server-integration"></a>Team Foundation Server 統合  
 作業項目をモデル要素にリンクし、リンクされた項目にプログラムでアクセスできます。  
  
 Fabrikam 社のツール開発者は、それぞれの空港プロジェクトの作業スケジュールを生成するツールを作成します。 スケジュールされた作業項目は、モデル要素にリンクされます。  
  
 詳細については、次を参照してください。[作業項目リンク ハンドラーを定義](../modeling/define-a-work-item-link-handler.md)します。  
  
## <a name="tools-that-update-models"></a>モデルを更新するツール  
 UML モデルの読み込みを行えるスタンドアロン アプリケーションと Visual Studio 拡張機能を作成できます。  
  
 Fabrikam 社の開発者は、モデルを読み取り、モデルの各要素での作業の進捗状況についてレポートを生成するツールを作成します。  
  
 詳細については、次を参照してください。[プログラム コードで UML モデルを読み取る](../modeling/read-a-uml-model-in-program-code.md)します。  
  
## <a name="domain-specific-languages"></a>ドメイン固有の言語  
 特定の種類のモデルを頻繁に使用する場合は、ドメイン固有の言語を作成しておくと便利です。 このようにすると UML モデルより密接にビジネス ニーズに合うものを作成できますが、それを構築して保守するには多大の労力が必要です。 詳細については、次を参照してください。 [Modeling SDK for Visual Studio - ドメイン固有言語](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)します。  
  
## <a name="external-resources"></a>外部リソース  
  
|**カテゴリ**|**リンク**|  
|------------------|---------------|  
|**ビデオ**|![ビデオへのリンク](../data-tools/media/playvideo.gif "PlayVideo") [MSDN How Do I シリーズ: UML ツールと機能拡張](http://go.microsoft.com/fwlink/?LinkId=214467)<br /><br /> ![ビデオへのリンク](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Visual Studio での UML](http://go.microsoft.com/fwlink/?LinkId=199957)|  
|**フォーラム**|-   [Visual Studio の視覚化ツールとモデリング ツール](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio の視覚化ツールとモデリング SDK (DSL ツール)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**ブログ**|[Visual Studio ALM + Team Foundation Server のブログ](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**技術記事とジャーナル**|[MSDN アーキテクチャ センター](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>関連項目  
 [アプリのモデルを作成します。](../modeling/create-models-for-your-app.md)   
 [UML モデリング機能拡張の API リファレンス](../modeling/api-reference-for-uml-modeling-extensibility.md)



