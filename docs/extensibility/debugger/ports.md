---
title: ポート |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77a0b954242a65e6f462a0548eeac0bc551e1083
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873607"
---
# <a name="ports"></a>ポート
デバッガーのアーキテクチャで、*ポート*:  
  
- サーバーで実行する一連のプロセスのコンテナー。 たとえば、ポートは、シリアル ケーブルで Windows CE ベース デバイスまたは DCOM 以外のネットワークに接続されたマシンへの接続を表すことができます。 ローカルのポートと呼ばれる 1 つの特殊なポートには、ローカル コンピューターで実行されているすべてのプロセスが含まれています。  
  
- 名前または識別子自体を識別できます。  
  
- できますとポートで実行されているすべてのプロセスを列挙し、起動し、これらのプロセスを終了します。  
  
- によって表される、 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)インターフェイスを渡すことによって作成される、 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)引数[AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)します。  
  
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] すべて Windows ベースのプロセス、ネイティブおよびマネージの両方を処理する既定のポートを提供します。 カスタム ポートは Windows ベースではない外部のデバイスとの接続を設定する必要があります。 このようなカスタム ポートを指定するもカスタム ポートのサプライヤーを設定する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [サーバー](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [プロセス](../../extensibility/debugger/processes.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)