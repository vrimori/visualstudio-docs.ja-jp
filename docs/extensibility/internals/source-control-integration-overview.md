---
title: ソース管理の統合の概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 19d75936e21729729dfeafaa041d800acbe01caa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-integration-overview"></a>ソース管理の統合の概要
このセクションでは、Visual Studio ソース コントロールに統合する 2 つの方法を比較します。ソース管理プラグインと、VSPackage をソース管理ソリューションを提供し、新しいソース管理機能を強調表示します。 Visual Studio をソース管理 Vspackage とソース管理プラグインの手動切り替えに従って自動ソリューションに基づく切り替えを使用します。  
  
## <a name="source-control-integration"></a>ソース管理の統合  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ソース管理の統合オプションの 2 つの種類をサポートしています。 すべてのバージョンで[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、プラグイン API に基づいて、ソース管理プラグイン (以前とも呼びます MSSCCI API)、Visual Studio ソース コントロールのユーザー インターフェイス (を使用しているときに、基本的なソース管理機能を提供することができますも統合UI)。 ソース コントロール VSPackage、その一方で、使用した、新しい深い統合[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]高いレベルの知識とそのソース コントロール モデルで自律性を確認要求するソース管理の統合に適したパス。  
  
 ![コントロールの概要をソース](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>ソース管理プラグイン  
 Visual Studio のすべてのバージョンでは、統合パスとして、ソース管理プラグイン API 仕様のバージョン 1.2 をサポートします。 ソース管理プラグイン実行者が」の説明に従って、ソース管理の統合および登録のソース管理プラグイン API 関数を実装する DLL を書き込みます[ソース管理プラグインを作成する](../../extensibility/internals/creating-a-source-control-plug-in.md)です。 統合開発環境 (IDE) を使用してこの方法で、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]で、チェック アウト、ツール/オプション プロパティ ページ、ツールバー、およびソース コントロールのグリフのチェックなどのダイアログ ボックスの UI。 ソース管理プラグイン API への厳密な準拠では、Visual Studio と、ユーザーにとって問題ない機能に簡単に統合が保証されます。 つまり、ソース管理プラグインは、ほとんどの関数と API の詳細なコールバックを実装する必要があります。  
  
 プラグイン ソース管理プラグイン API を使用してソース管理を実装するのには、次の手順を実行します。  
  
1.  指定された関数を実装する DLL を作成する[ソース管理プラグイン](../../extensibility/source-control-plug-ins.md)です。  
  
2.  DLL を登録するには、適切なレジストリ エントリを作成する (記載[する方法: ソース管理プラグインをインストール](../../extensibility/internals/how-to-install-a-source-control-plug-in.md))。  
  
3.  UI とソース管理アダプター パッケージ (ソース管理プラグインを使用してソース管理機能を処理する Visual Studio コンポーネント) によってメッセージが表示されたら、表示、ヘルパーを作成します。  
  
 、ソース管理のコマンドに応答、Visual Studio IDE 基本的な操作の標準的な UI を表示し、渡します情報をソース管理にプラグイン ソース管理プラグイン API で定義された関数を使用しています。 高度なオプションは、ソース管理プラグインで呼び出すことは、独自の UI を表示するなど、ソース管理プロジェクトの参照します。 つまり、ユーザーが表示される場合 UI の 2 つの異なる場合もあるスタイルを使用してソース管理を処理する場合: Visual Studio に表示する UI と、ソース管理プラグインを表す UI です。 これは、高度なソース管理操作に顕著です。  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>ソース管理プラグインを実装するための短所があります。  
  
-   高度な機能は、ユーザーことがありますを参照してください、インターフェイスの 2 つの異なるスタイル混同につながるです。  
  
-   ソース管理プラグインは、ソース管理プラグイン API が含まれるソース制御モデルに限定します。  
  
-   ソース管理プラグイン API は、ソース管理のシナリオはいくつかの制限が多すぎて可能性があります。  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>ソース管理プラグインを実装する利点  
  
-   Visual Studio では、ソース管理プラグインが可能性のある複雑な UI を実装する必要がないように、すべての基本的なソース管理操作のすべての UI が用意されています。  
  
-   厳密な API のためソース管理プラグイン簡単に対話できる; より広範な機能を提供する外部のソース管理プログラムVisual Studio は、すぎるはるかソース管理機能の実現方法が、ソース管理プラグイン API に従ってこれを行うにはそれだけでも気にしません。  
  
-   ソース管理 VSPackage よりプラグイン ソース管理を実装しやすくなります。  
  
## <a name="source-control-vspackage"></a>ソース コントロールの VSPackage  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Visual Studio ソース管理機能を完全に制御し、Visual Studio に用意されているソース制御ユーザー インターフェイスの完全な置き換えと緊密に統合できます。 ソース管理 VSPackage は Visual Studio に登録され、ソース管理機能を提供します。 Visual Studio には、いくつかのソース管理の Vspackage を登録することができますがうちの 1 つのみを有効にする任意の時点です。 ソース管理 VSPackage に、ソース管理機能と外観を完全に制御 Visual Studio ではアクティブであります。 他のすべてのソース管理システムに登録することがある Vspackage は、アクティブではありませんし、UI をまったく表示されません。  
  
 ソース制御 VSPackage を実装するには、「すべてまたは nothing」の戦略が必要です。 ソース管理の VSPackage の作成者は、さまざまなソース コントロールのインターフェイスと (ダイアログ ボックス、メニューのおよびツールバー) 全体のソース管理機能をカバーする新しい UI 要素を実装する作業量を大幅をかける必要があります。 参照してください[ソース コントロールの VSPackage を作成する](../../extensibility/internals/creating-a-source-control-vspackage.md)詳細についてはします。  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>ソース コントロールの VSPackage の実装の欠点  
  
-   VSPackage では、Visual Studio で正常に統合する複雑なインターフェイスの数を実装する必要があります。  
  
-   VSPackage がソース管理されているために必要なすべての UI を指定する必要があります。Visual Studio で、この領域にアシスタンスを提供するものはありません。  
  
-   ソース管理 VSPackage は、Visual Studio には、密接し、機能は、外部プログラムのバージョン、ソース コントロールと同じくらい簡単に共有できないように、スタンドアロン プログラムで操作できません。  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>ソース コントロールの VSPackage を実装する利点  
  
-   VSPackage は、ソース管理 UI を完全に制御および機能があるために、ソース管理のためのシームレスなインターフェイスで、ユーザーが表示されます。  
  
-   VSPackage は、特定のソース コントロールのモデルに限定されていません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理](../../extensibility/internals/source-control.md)   
 [ソース管理プラグインを作成します。](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [ソース コントロールの VSPackage の作成](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [ソース管理の新機能](../../extensibility/internals/what-s-new-in-source-control.md)