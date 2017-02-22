---
title: "ポート | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ポート"
  - "[デバッグの SDK] をデバッグするには、ポートします。"
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# ポート
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッガーのアーキテクチャという点では **ポート** :  
  
-   一連のサーバーで実行されているプロセスのコンテナーです。  たとえばシリアル ポートはネットワーク ケーブルがまたは非 DCOM マシンへの接続を Windows CE ベースのデバイスを表すことがあります。  ローカル ポートという 1 種類の特別なポートがローカル コンピューターで実行しているすべてのプロセスが含まれています。  
  
-   自身または識別子を名前で指定できます。  
  
-   ポートで実行されているプロセスを列挙しこれらのプロセスを開始および終了できます。  
  
-   [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) に [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) の引数を渡すことによって作成された [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) のインターフェイスで表されます。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] はすべての Windows ベースのプロセス \(ネイティブおよびマネージ\) を処理する既定のを指定します。  カスタム ポートはWindows ベースではない外部デバイスを使用して接続に対して実行する必要があります。  このようなカスタム ポートを実装するカスタム ポートの仕入先を指定する必要があります。  
  
## 参照  
 [サーバー](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [プロセス](../../extensibility/debugger/processes.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)