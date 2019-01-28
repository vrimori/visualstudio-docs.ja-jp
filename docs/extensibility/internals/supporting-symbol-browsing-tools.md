---
title: シンボル参照ツールのサポート |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d051809d02624f686f3ffc5408441d18e890854
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001486"
---
# <a name="supporting-symbol-browsing-tools"></a>シンボル参照ツールのサポート
**オブジェクト ブラウザー**、**クラス ビュー**、**呼び出しブラウザー**と**シンボルの検索結果**ツールは Visual Studio での機能を参照するシンボルを提供します。 これらのツールでは、シンボルの階層ツリー ビューを表示し、ツリー内のシンボルの関係を表示します。 シンボルは、名前空間、オブジェクト、クラス、クラスのメンバー、およびさまざまなコンポーネントに含まれるその他の言語要素を表すことがあります。 コンポーネントには、Visual Studio プロジェクトに外部[!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)]コンポーネントとタイプ (.tlb) ライブラリ。 詳細については、「[コードの構造の表示](../../ide/viewing-the-structure-of-code.md)」を参照してください。  
  
## <a name="symbol-browsing-libraries"></a>シンボル参照のライブラリ  
 言語実装者は、コンポーネント内のシンボルを追跡し、一連のインターフェイスを通じて、Visual Studio オブジェクト マネージャーにシンボルのリストを提供するライブラリを作成して、Visual Studio のシンボル参照の機能を拡張できます。 ライブラリは、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2>インターフェイス。 Visual Studio のオブジェクト マネージャーでは、ライブラリからデータを取得し、整理することによって、シンボル参照ツールから新しいデータの要求に応答します。 後で、設定します。 または、要求されたデータでツールを更新します。 Visual Studio オブジェクト マネージャーへの参照を取得する<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>、渡す、<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager>サービス ID に、`GetService`メソッド。  
  
 各ライブラリは、すべてのライブラリを情報を収集する Visual Studio オブジェクト マネージャーを登録する必要があります。 ライブラリを登録するには、呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>メソッド。 によって、どのツールを開始すると、要求は、Visual Studio のオブジェクト マネージャーは、適切なライブラリを検索し、データを要求します。 ライブラリ間のデータを移動し、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]オブジェクト マネージャーで説明されているシンボルの一覧で、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>インターフェイス。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]オブジェクト マネージャーは、ライブラリに含まれている最新のデータを反映するように、シンボル参照ツールを定期的に更新する責任を負います。  
  
 次の図には、ライブラリと、Visual Studio のオブジェクト マネージャー間で要求/データの交換プロセスの主要な要素のサンプルが含まれています。 図で示されるインターフェイスは、マネージ コード アプリケーションの一部です。  
  
 ![ライブラリとオブジェクト マネージャー間のデータ フロー](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 シンボルのリストを Visual Studio のオブジェクト マネージャーを提供する必要がありますまずライブラリを登録する、Visual Studio のオブジェクト マネージャーで呼び出すことによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>メソッド。 ライブラリが登録されると、Visual Studio のオブジェクト マネージャーは、ライブラリの機能に関する特定の情報を要求します。 たとえば、ライブラリ フラグを要求し、カテゴリを呼び出すことによってサポートされている、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A>メソッド。 いくつかの時点では、このライブラリでは、データを要求、ツールの 1 つと、オブジェクト マネージャー シンボルの最上位レベルの一覧を呼び出して要求、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A>メソッド。 応答として、ライブラリのシンボルの一覧を製造およびを通じて Visual Studio のオブジェクト マネージャーに公開する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>インターフェイス。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]オブジェクト マネージャーの決定項目の数が呼び出すことによって、一覧では、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A>メソッド。 次のすべての要求では、リスト内の特定の項目に関連付けられており、各要求で、項目のインデックス番号を指定します。 Visual Studio のオブジェクト マネージャーが、種類、アクセシビリティ、およびその他の項目のプロパティを呼び出すことによって、情報を収集する処理、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A>メソッド。  
  
 呼び出すことによって、アイテムの名前を決定しますが、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A>メソッドを呼び出してアイコンの情報を要求し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A>メソッド。 アイコンは、項目名の左側に表示され、項目、アクセシビリティ、およびその他のプロパティの型を示しています。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]オブジェクト マネージャーを呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A>する特定のリスト項目が展開され、子項目があるかどうかを判断するメソッド。 オブジェクト マネージャーが呼び出すことによって子シンボルの一覧を要求する UI は、要素を拡張する要求を送信する場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A>メソッド。 プロセスは、オンデマンドで構築されるツリーのさまざまな部分を続行します。  
  
> [!NOTE]
>  ネイティブ コードのシンボル プロバイダーを実装するには、使用、<xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2>インターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [方法: オブジェクト マネージャーにライブラリを登録します。](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [方法: オブジェクト マネージャーにライブラリによって提供されるシンボルのリストを公開します。](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [方法: ライブラリ内のシンボルを識別します。](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)