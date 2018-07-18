---
title: シンボル参照のツールのサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08185f64310da610253dc35e69323b17ab0177fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134592"
---
# <a name="supporting-symbol-browsing-tools"></a>シンボル参照のツールのサポート
**オブジェクト ブラウザー**、**クラス ビュー**、**呼び出しブラウザー**と**シンボルの検索結果**ツールは、シンボル参照 Visual Studio での機能を提供します。 これらのツールは、シンボルの階層ツリー ビューを表示し、ツリー内のシンボルの関係を表示します。 シンボルには、名前空間、オブジェクト、クラス、クラス メンバー、およびさまざまなコンポーネントに含まれるその他の言語要素を表すことがあります。 コンポーネントは、Visual Studio プロジェクトは、外部[!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)]コンポーネントおよび (.tlb) のタイプ ライブラリ。 詳細については、「[コードの構造の表示](../../ide/viewing-the-structure-of-code.md)」を参照してください。  
  
## <a name="symbol-browsing-libraries"></a>シンボル参照のライブラリ  
 言語の実行者、コンポーネント内のシンボルを追跡し、一連のインターフェイスの使用は、Visual Studio オブジェクト マネージャーにシンボルのリストを提供するライブラリを作成することで、Visual Studio のシンボル参照機能を拡張できます。 ライブラリは、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2>インターフェイスです。 Visual Studio は、オブジェクト マネージャーでは、ライブラリからデータを取得して、それを整理して、シンボル参照のツールから新しいデータの要求に応答します。 後で、設定または、ツールを要求されたデータに更新されます。 Visual Studio オブジェクト マネージャーへの参照を取得する<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>、渡す、<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager>サービス ID に、`GetService`メソッドです。  
  
 各ライブラリは、すべてのライブラリを情報を収集する Visual Studio オブジェクト マネージャーを登録する必要があります。 ライブラリを登録するには、呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>メソッドです。 どのツールを開始すると、要求、によっては、Visual Studio は、オブジェクト マネージャーは、適切なライブラリを検索して、データを要求します。 ライブラリ間でデータが転送され、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]オブジェクト マネージャーで記述されるシンボルの一覧で、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>インターフェイスです。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]オブジェクト マネージャーは、ライブラリに格納されている最新のデータを反映するようにツールのシンボル参照を定期的に更新します。  
  
 次の図には、ライブラリと、Visual Studio オブジェクト マネージャー間で要求/データの交換プロセスの主要な要素のサンプルが含まれています。 ダイアグラム内のインターフェイスは、マネージ コード アプリケーションの一部です。  
  
 ![ライブラリとオブジェクト マネージャー間のデータ フロー](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Visual Studio は、オブジェクト マネージャーにシンボルのリストを提供する必要があります最初ライブラリを登録する Visual Studio は、オブジェクト マネージャーで呼び出すことによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>メソッドです。 ライブラリが登録されると、Visual Studio は、オブジェクト マネージャーは、ライブラリの機能に関する特定の情報を要求します。 たとえば、ライブラリ フラグを要求し、カテゴリを呼び出すことによってサポートされている、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A>メソッドです。 ある時点で、このライブラリからデータを要求、ツールのいずれかと、オブジェクト マネージャー要求シンボルの最上位のリストを呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A>メソッドです。 応答として、ライブラリの記号の一覧を製造および、Visual Studio オブジェクト マネージャーを介して公開する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>インターフェイスです。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]オブジェクト マネージャーの決定項目の数が呼び出すことによって、一覧には、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A>メソッドです。 次のすべての要求は、リスト内の特定のアイテムに関連し、各要求の項目のインデックス番号を指定します。 呼び出して、型、アクセシビリティ、およびその他の項目のプロパティで情報を収集する Visual Studio は、オブジェクト マネージャーが続行されます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A>メソッドです。  
  
 呼び出して、項目の名前を決定、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A>メソッドを呼び出してアイコンの情報を要求し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A>メソッドです。 アイコンは、項目名の左側に表示され、アイテム、アクセシビリティ、およびその他のプロパティの型を示しています。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]オブジェクト マネージャーの呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A>メソッドを指定されたリスト項目が展開され、子項目があるかどうかを判断します。 UI 要素を展開する要求を送信する場合、オブジェクト マネージャー、子の一覧を要求シンボルを呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A>メソッドです。 プロセスは、要求時に構築される、ツリーのさまざまな部分を続行します。  
  
> [!NOTE]
>  ネイティブ コードのシンボル プロバイダーを実装するには、使用、<xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2>インターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [方法: オブジェクト マネージャーにライブラリを登録](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [方法: オブジェクト マネージャーにライブラリによって提供されるシンボルのリストを公開](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [方法: ライブラリでのシンボルの識別](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)