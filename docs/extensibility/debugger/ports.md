---
title: "ポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 926f5e9a80a91da57d843c11175865f78775e38c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ports"></a>ポート
デバッガーのアーキテクチャの観点から、**ポート**:  
  
-   サーバーで実行するプロセスのセットのコンテナーです。 たとえば、ポートは、シリアル ケーブルの場合は、Windows CE ベースのデバイスまたは DCOM 以外のネットワークに接続されたコンピューターの接続を表す場合があります。 ローカルのポートと呼ばれる 1 つの特殊なポートには、ローカル コンピューターで実行されているすべてのプロセスが含まれています。  
  
-   名前または識別子をそれ自体を特定できます。  
  
-   できますとポートで実行されているすべてのプロセスを列挙し、起動し、これらのプロセスを終了します。  
  
-   によって表される、 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)を渡すことによって作成されるインターフェイス、 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)引数[AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)です。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]すべて Windows ベースのプロセス、ネイティブおよびマネージを処理する既定のポートを指定します。 Windows ベースではない外部のデバイスでは、接続のカスタム ポートを実装しなければなりません。 このようなカスタム ポートを指定するには、カスタム ポート業者も実装する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [サーバー](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [プロセス](../../extensibility/debugger/processes.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)