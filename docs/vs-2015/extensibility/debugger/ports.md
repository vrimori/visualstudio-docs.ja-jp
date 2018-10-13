---
title: ポート |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f637c348295e709698d710016c80aa717613a068
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281763"
---
# <a name="ports"></a>ポート
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

デバッガーのアーキテクチャの観点から、**ポート**:  
  
-   サーバーで実行する一連のプロセスのコンテナー。 たとえば、ポートは、シリアル ケーブルの場合は、Windows CE ベース デバイスまたは DCOM 以外のネットワークに接続されたマシンへの接続を表すことができます。 ローカルのポートと呼ばれる 1 つの特殊なポートには、ローカル コンピューターで実行されているすべてのプロセスが含まれています。  
  
-   名前または識別子自体を識別できます。  
  
-   できますとポートで実行されているすべてのプロセスを列挙し、起動し、これらのプロセスを終了します。  
  
-   によって表される、 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)インターフェイスを渡すことによって作成される、 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)引数[AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)します。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] すべて Windows ベースのプロセス、ネイティブおよびマネージを処理する既定のポートを提供します。 Windows ベースではない外部のデバイスでは、接続のカスタム ポートを実装しなければなりません。 このようなカスタム ポートを指定するには、カスタム ポート サプライヤーは実装にも必要です。  
  
## <a name="see-also"></a>関連項目  
 [サーバー](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [プロセス](../../extensibility/debugger/processes.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

