---
title: ソース管理の統合の概要 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ca8fc2368fd2da031342cf76ab7ba9abb85e6f4b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540116"
---
# <a name="source-control-integration-overview"></a>ソース管理の統合の概要
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ソース管理の統合の概要](https://docs.microsoft.com/visualstudio/extensibility/internals/source-control-integration-overview)します。  
  
このセクションでは、Visual Studio ソース コントロールに統合する 2 つの方法を比較します。ソース管理プラグインと、VSPackage をソース管理のソリューションを提供し、新しいソース管理機能を強調表示されます。 Visual Studio は、ソース管理 Vspackage とソース管理プラグインの切り替えを手動と自動のソリューションに基づく切り替えできます。  
  
## <a name="source-control-integration"></a>ソース管理の統合  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ソース管理の統合オプションの 2 つの種類をサポートしています。 すべてのバージョンの[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、プラグイン API に基づくソース管理プラグイン (以前別名 MSSCCI API として)、Visual Studio ソース コントロールのユーザー インターフェイス (を使用しているときに、基本的なソース管理機能を提供することができますも統合UI の場合)。 ソース管理 VSPackage では、その一方で、新しい、深い統合を提供[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]面の知識と、ソース管理モデルでの自律性の高いレベルの要求のソース管理の統合に適したパス。  
  
 ![コントロールの概要をソース](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>ソース管理プラグイン  
 Visual Studio のすべてのバージョンでは、統合パスとして、ソース管理プラグイン API 仕様バージョン 1.2 をサポートします。 ソース管理プラグイン実行者が」の説明に従って、ソース管理の統合と登録のソース管理プラグイン API 関数を実装する DLL を書き込みます[をソース管理プラグインを作成する](../../extensibility/internals/creating-a-source-control-plug-in.md)します。 この方法で統合開発環境 (IDE) を使用して、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]チェックイン、チェック アウト、プロパティ ページの [ツール] メニュー、ツールバー、およびソース コントロールのグリフのなどのダイアログ ボックスの UI。 ソース管理プラグイン API への厳密な準拠では、Visual Studio と問題のない、ユーザー エクスペリエンスに簡単に統合が保証されます。 つまり、ソース管理プラグインは、ほとんどの機能と API の詳細なコールバックを実装する必要があります。  
  
 ソース コントロールが、ソース管理プラグイン API を使用してプラグインを実装するには、次の手順に従います。  
  
1.  指定された関数を実装する DLL を作成する[ソース管理プラグイン](../../extensibility/source-control-plug-ins.md)します。  
  
2.  DLL を登録するには、適切なレジストリ エントリを作成する (で説明されている[方法: ソース管理のプラグインをインストール](../../extensibility/internals/how-to-install-a-source-control-plug-in.md))。  
  
3.  UI と表示のソース管理アダプター パッケージ (ソース管理プラグインを使用してソース管理機能を処理する Visual Studio コンポーネント) のメッセージが表示されたら、ヘルパーを作成します。  
  
 ソース管理のコマンドに応答して、Visual Studio IDE の基本的な操作の標準的な UI を表示し、渡します情報をソース管理プラグイン、ソース管理プラグイン API で定義された関数を使用しています。 高度なオプションは、ソース管理プラグインを呼び出すことで、独自の UI を表示するのになどのソース管理プロジェクトの参照します。 つまり、ソース管理を処理するとき、ユーザーを UI の 2 つの異なるスタイルで表示可能性があること: Visual Studio によって提示される UI と UI をソース管理プラグインを表示します。 高度なソース管理操作で最も目立つようになります。  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>欠点は、ソース管理プラグインを実装します。  
  
-   高度な機能は、のユーザーは、特定できるだけ混乱につながる、インターフェイスの 2 つの異なるスタイルを表示可能性があります。  
  
-   ソース管理プラグインは、ソース管理プラグイン API が含まれるソース コントロールのモデルに限定されます。  
  
-   ソース コントロールのプラグイン API は、ソース管理のシナリオはいくつかの制限が多すぎて可能性があります。  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>ソース管理プラグインを実装する利点  
  
-   Visual Studio では、ソース管理プラグインが可能性のある複雑な UI を実装する必要がないように、すべての基本的なソース管理操作のすべての UI が用意されています。  
  
-   ため、厳密な API をソース管理プラグインはより広範な機能を提供する外部のソース管理プログラムと対話簡単にできます。Visual Studio は、すぎるはるかソース管理の機能を実現する方法、ソース管理プラグイン API に従って方法、その場合はそれだけでも気にしません。  
  
-   ソース管理 VSPackage よりプラグイン ソース管理を実装するために簡単です。  
  
## <a name="source-control-vspackage"></a>ソース管理 VSPackage  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Visual Studio のソース管理機能を完全に制御し、Visual Studio で提供されるソース制御ユーザー インターフェイスの完全な置き換えを緊密に統合できます。 ソース管理 VSPackage は Visual Studio に登録され、ソース管理機能を提供します。 Visual Studio には、いくつかのソース管理 Vspackage を登録することができますが 1 つだけを有効にする任意の時点。 ソース管理 VSPackage がアクティブな Visual Studio でソース管理機能と外観を完全に制御が。 他のすべてのソース管理システムに登録することがあります Vspackage では、アクティブでないし、UI をまったく表示されません。  
  
 ソース管理 VSPackage の実装には、「全部かゼロか」の戦略が必要です。 ソース管理 VSPackage の作成者は、さまざまなソース コントロールのインターフェイスと (ダイアログ ボックス、メニューのおよびツールバー) 全体のソースの管理機能をカバーする、新しい UI 要素を実装する作業量が大幅に投資する必要があります。 参照してください[ソース管理 VSPackage を作成する](../../extensibility/internals/creating-a-source-control-vspackage.md)の詳細。  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>ソース管理 VSPackage の実装の欠点  
  
-   VSPackage では、さまざまな Visual Studio と正常に統合する複雑なインターフェイスを実装する必要があります。  
  
-   VSPackage は、ソース管理されているために必要なすべての UI を提供する必要があります。Visual Studio で、この領域についての支援を提供するものはありません。  
  
-   ソース管理 VSPackage は、Visual Studio には密接し、機能は外部のバージョン、ソース管理プログラムのように簡単に共有できないようにスタンドアロンのプログラムで操作できません。  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>ソース管理 VSPackage を実装する利点  
  
-   VSPackage はソース管理 UI を完全に制御し、機能があるために、ソース管理のためのシームレスなインターフェイスで、ユーザーが表示されます。  
  
-   VSPackage は、特定のソース コントロールのモデルに限定されていません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理](../../extensibility/internals/source-control.md)   
 [ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [ソース管理 VSPackage を作成します。](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [ソース管理の新機能](../../extensibility/internals/what-s-new-in-source-control.md)

