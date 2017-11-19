---
title: "グローバル設定を監視するテキスト マネージャーを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9687e4f0be16fb42f13c6f9dd20a2cb39be50cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>テキスト マネージャーを使用して、グローバル設定を監視するには
コア エディターを実装すると場合、は、これらの変更は、エディターのインスタンスを与える可能性がありますので、グローバル設定に加えられた変更を監視する必要があります。 変更を追跡するには、テキスト マネージャーによって生成されるイベントをリッスンしています。 たとえば、コア エディターで、そのドキュメント データ オブジェクトなどの表示やコンポーネントの動作のグローバル設定を指定するときにテキスト マネージャーはこの情報を格納し、影響を受けるすべてのクライアントに通信します。  
  
## <a name="text-manager-functions"></a>テキスト マネージャー関数  
 テキスト マネージャーは、いくつかの設定は、次のようにイベントを発生させます。  
  
-   バッファーはソース コード管理下にある、かどうか  
  
-   ファイル変更通知を登録する方法  
  
-   どのビューは、特定のバッファーに関連付けられているを追跡する方法  
  
-   テキストの色づけの基本設定  
  
-   タブ領域の基本設定との比較  
  
 特定の言語に固有の設定は、テキスト マネージャーで管理されていません。 これらの設定は、各言語サービスで管理する必要があります。  
  
 テキスト マネージャーのイベント通知は、によって提供される、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>インターフェイスです。 このインターフェイスを実装して、クライアントでテキスト マネージャーに発生するイベントを処理するオブジェクト。 使用してこれらのイベントの登録、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>テキスト マネージャー上のインターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [コア エディター内](../extensibility/inside-the-core-editor.md)   
 [エディターの機能](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)