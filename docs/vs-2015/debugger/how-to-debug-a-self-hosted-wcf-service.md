---
title: '方法: 自己ホスト型 WCF サービスのデバッグ |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec8f1fee46a1df931842992df1daa38942ca07bc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182248"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>方法 : セルフホストされている WCF サービスをデバッグする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A*自己ホスト型サービス*WCF サービス、WCF サービス ホストを IIS 内で実行していない、または[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]開発サーバーです。 自己ホスト型 WCF をデバッグする最も簡単な方法は、構成することです。[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]を選択すると、クライアントとサーバーの両方を起動する**デバッグの開始**上、**デバッグ**メニュー。  
  
 NT サービスなど、この方法で起動できないプロセス内部で WCF サービスがセルフホストされている場合、この手法は使用できません。 代わりに、次の方法のいずれかを使用できます。  
  
-   ホスト プロセスにデバッガーを手動でアタッチします。 詳細については、次を参照してください。[実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)します。  
  
     または  
  
-   クライアントでデバッグを開始し、次にサービスへの呼び出しにステップ インします。 これを行うには、app.config ファイルでデバッグを有効にする必要があります。 詳細については、 [WCF デバッグの制約](../debugger/limitations-on-wcf-debugging.md)します。  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>Visual Studio からクライアントとホストの両方を起動するには  
  
1.  クライアント プロジェクトとサーバー プロジェクトの両方を含む [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ソリューションを作成します。  
  
2.  選択したときに、クライアントとサーバーの両方のプロセスを開始するソリューションの構成**開始**上、**デバッグ**メニュー。  
  
    1.  **ソリューション エクスプ ローラー**ソリューション名を右クリックします。  
  
    2.  クリックして**スタートアップ プロジェクトを設定**します。  
  
    3.  **ソリューション\<名 > プロパティ**ダイアログ ボックスで、**マルチ スタートアップ プロジェクト**します。  
  
    4.  **マルチ スタートアップ プロジェクト**、サーバー プロジェクトに対応する行で、グリッドのクリックして**アクション**選択**開始**。  
  
    5.  クライアント プロジェクトに対応する行をクリックして**アクション**選択**開始**します。  
  
    6.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [WCF サービスのデバッグ](../debugger/debugging-wcf-services.md)   
 [WCF デバッグの制約](../debugger/limitations-on-wcf-debugging.md)   
 [方法 : WCF サービスにステップ インする](../debugger/how-to-step-into-wcf-services.md)



