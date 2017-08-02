---
title: "ソース管理の統合の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d3facc06885ef927448eb506ff2f4aa5c04ce85f
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-integration-overview"></a>ソース管理の統合の概要
このセクションでは、Visual Studio ソース コントロールに統合する&2; つの方法を比較します。ソース管理プラグインと VSPackage をソース管理ソリューションを提供し、新しいソース管理機能を強調表示します。 ソース管理 VSPackages とソース管理プラグインの手動切り替えと自動ソリューションに基づく切り替えの visual Studio を使用します。  
  
## <a name="source-control-integration"></a>ソース管理の統合  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース管理の統合オプションの&2; つの種類をサポートしています。 すべてのバージョンの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、統合することも、ソース管理プラグイン API に基づいて以前 (MSSCCI API として)、Visual Studio のソース コントロールのユーザー インターフェイス (UI) を使用しているときに、基本的なソース管理機能を提供するプラグイン。 ソース管理、VSPackage がこれに対して、新しい、詳細な統合を提供[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]高レベルの先進的な機能とそのソース制御モデルでの自律性を確認要求するソース管理の統合に適したパスです。  
  
 ![コントロールの概要をソース](~/extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>ソース管理プラグイン  
 Visual Studio のすべてのバージョンでは、統合パスとしてソース管理プラグインの API 仕様バージョン 1.2 をサポートします。 ソース管理プラグイン実行者が」の説明に従って、ソース管理の統合と登録のソース管理プラグインの API 関数を実装する DLL を書き込みます[ソース管理プラグインを作成する](../../extensibility/internals/creating-a-source-control-plug-in.md)です。 この方法で統合開発環境 (IDE) を使用して、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]チェックイン、チェック アウト、ツール/オプションのプロパティ ページ、ツールバー、およびソース コントロールのグリフのなどのダイアログ ボックスの UI です。 ソース コントロールのプラグイン API への厳密な準拠では、Visual Studio と問題のない、ユーザー エクスペリエンスに簡単に統合が保証されます。 つまり、ソース管理プラグインは、ほとんどの関数と API の詳細なコールバックを実装する必要があります。  
  
 ソース管理プラグインの API を使用してプラグインのソース管理を実装するのには、次の手順を実行します。  
  
1.  指定された関数を実装する DLL を作成する[ソース管理プラグイン](../../extensibility/source-control-plug-ins.md)します。  
  
2.  適切なレジストリ エントリを作成して DLL を登録 (で説明されている[方法: ソース管理プラグインをインストール](../../extensibility/internals/how-to-install-a-source-control-plug-in.md))。  
  
3.  UI とソース管理アダプター パッケージ (ソース管理プラグインを使用してソース管理機能を処理する Visual Studio コンポーネント) が表示されたときに表示するヘルパーを作成します。  
  
 ソース管理のコマンドに応答して、Visual Studio IDE の基本的な操作のための標準 UI を表示し、渡します情報をソース管理プラグイン ソース コントロールのプラグイン API で定義された関数を使用しています。 高度なオプションは、ソース管理プラグイン呼び出すことができますに独自の UI を表示するなどのソース管理プロジェクトを参照します。 これは、ソース管理を処理する場合、ユーザーを UI の&2; つの異なるスタイルを使用して記述するあることを意味します。 Visual Studio は、UI と、ソース管理プラグインを表示する UI。 これは、高度なソース管理操作で最も顕著です。  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>ソース管理プラグインを実装することの欠点  
  
-   高度な機能、ユーザーは、特定できるだけ混乱につながる、インターフェイスの&2; 種類のスタイルを参照可能性があります。  
  
-   ソース管理プラグインは、ソース管理プラグインの API が含まれるソース コントロール モデルに限定されます。  
  
-   ソース管理プラグインの API をいくつかのソース管理のシナリオよりも制限が厳しすぎることがあります。  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>ソース管理プラグインを実装する利点  
  
-   Visual Studio では、ソース管理プラグインが可能性のある複雑な UI を実装する必要がないように、すべての基本的なソース管理操作のすべての UI が用意されています。  
  
-   厳密な API により、ソース管理プラグインできますを容易にやり取りより広範な機能を提供する外部のソース管理プログラムVisual Studio は、すぎるずっとソース管理機能を実現する方法、ソース コントロールのプラグイン API に従って行いますはそれだけを処理していません。  
  
-   ソース管理 VSPackage よりプラグインのソース管理を実装しやすくなります。  
  
## <a name="source-control-vspackage"></a>ソース コントロールの vs パッケージ  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]ソース管理機能を完全に制御し、Visual Studio から提供されるソース制御ユーザー インターフェイスの完全な置き換えを Visual Studio に深く統合できます。 ソース管理 VSPackage が Visual Studio に登録されており、ソース管理機能を提供します。 いくつかのソース管理 VSPackages は、Visual Studio に登録できる、そのうち片方だけを有効にする任意の時点です。 ソース コントロールは、VSPackage がアクティブなときに、Visual Studio でソース管理機能と外観を完全に制御を持ちます。 その他のすべてのソース管理システムに登録することがある Vspackage はアクティブで、任意の UI をまったく表示されないれます。  
  
 ソース管理 VSPackage を実装するには、「全か無か」の戦略が必要です。 ソース管理 VSPackage の作成者は、さまざまなソース コントロールのインターフェイスと (ダイアログ ボックス、メニューのおよびツールバー) 全体のソース管理機能をカバーする、新しい UI 要素の実装の開発作業量が大幅にかける必要があります。 参照してください[ソース コントロール VSPackage を作成する](../../extensibility/internals/creating-a-source-control-vspackage.md)詳細です。  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>ソース コントロール VSPackage を実装することの欠点  
  
-   VSPackage では、さまざまな Visual Studio で正常に統合する複雑なインターフェイスを実装する必要があります。  
  
-   VSPackage でソース管理されているために必要なすべての UI を提供する必要があります。Visual Studio はこの領域内でのサポートを提供しないします。  
  
-   ソース管理 VSPackage は Visual Studio には、密接し、機能は、ソース管理プログラムの外部のバージョンと同じくらい簡単に共有できないように、スタンドアロン プログラムで操作できません。  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>ソース コントロール VSPackage を実装する利点  
  
-   VSPackage では、ソース管理 UI を完全に制御と機能を持っているので、ソース管理のためのシームレスなインターフェイスを持つユーザーが表示されます。  
  
-   VSPackage では、特定のソース制御モデルに限定されていません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理](../../extensibility/internals/source-control.md)   
 [ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [ソース コントロール VSPackage を作成します。](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [ソース管理の新機能します。](../../extensibility/internals/what-s-new-in-source-control.md)
