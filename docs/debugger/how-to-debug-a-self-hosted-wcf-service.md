---
title: "方法: 自己ホスト型 WCF サービスをデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e64f764153106c252ba1a9586bfd0a33f4e239f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>方法 : セルフホストされている WCF サービスをデバッグする
A*セルフホストされているサービス*する WCF サービスを IIS で WCF サービス ホスト内で実行されないのは、または[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]開発サーバーです。 自己ホスト型 WCF をデバッグする最も簡単な方法を構成するのには、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を選択すると、クライアントとサーバーの両方を起動する**デバッグの開始**上、**デバッグ**メニュー。  
  
 NT サービスなど、この方法で起動できないプロセス内部で WCF サービスがセルフホストされている場合、この手法は使用できません。 代わりに、次の方法のいずれかを使用できます。  
  
-   ホスト プロセスにデバッガーを手動でアタッチします。 詳細については、次を参照してください。[実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)です。  
  
     — または —  
  
-   クライアントでデバッグを開始し、次にサービスへの呼び出しにステップ インします。 これを行うには、app.config ファイルでデバッグを有効にする必要があります。 詳細については、 [WCF デバッグの制約](../debugger/limitations-on-wcf-debugging.md)です。  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>Visual Studio からクライアントとホストの両方を起動するには  
  
1.  クライアント プロジェクトとサーバー プロジェクトの両方を含む [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソリューションを作成します。  
  
2.  選択すると、クライアントとサーバーの両方のプロセスを開始するようにソリューションを構成する**開始**上、**デバッグ**メニュー。  
  
    1.  **ソリューション エクスプ ローラー**ソリューション名を右クリックします。  
  
    2.  をクリックして**スタートアップ プロジェクトの設定**です。  
  
    3.  **ソリューション\<名 > プロパティ**ダイアログ ボックスで、**マルチ スタートアップ プロジェクト**です。  
  
    4.  **マルチ スタートアップ プロジェクト**グリッドで、サーバー プロジェクトに対応する行で、をクリックして**アクション**選択**開始**です。  
  
    5.  クライアント プロジェクトに対応する行をクリックして**アクション**選択**開始**です。  
  
    6.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [WCF サービスのデバッグ](../debugger/debugging-wcf-services.md)   
 [WCF のデバッグに関する制限事項](../debugger/limitations-on-wcf-debugging.md)   
 [方法 : WCF サービスにステップ インする](../debugger/how-to-step-into-wcf-services.md)