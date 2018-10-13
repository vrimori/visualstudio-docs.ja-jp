---
title: WCF デバッグの制約 |Microsoft Docs
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
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e28ee8c4fa17eca8f2b5419b1d9aefb229fd020
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49219155"
---
# <a name="limitations-on-wcf-debugging"></a>WCF デバッグの制約
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WCF サービスのデバッグを開始するには、次の 3 つの方法があります。  
  
-   サービスを呼び出すクライアント プロセスをデバッグします。 デバッガーがサービスにステップ インします。 サービスは、クライアント アプリケーションと同じソリューションになくてもかまいません。  
  
-   サービスを要求するクライアント プロセスをデバッグします。 サービスは、ソリューションの一部である必要があります。  
  
-   使用する**プロセスにアタッチ**を現在実行中のサービスにアタッチします。 サービス内部でデバッグが開始されます。  
  
 このトピックでは、これらのシナリオの制約について説明します。  
  
## <a name="limitations-on-stepping-into-a-service"></a>サービスへのステップ インの制約  
 デバッグ中のクライアント アプリケーションのサービスにステップ インするには、次の条件を満たす必要があります。  
  
-   クライアントは、同期クライアント オブジェクトを使用してサービスを呼び出す必要があります。  
  
-   コントラクト操作では、一方向の操作を使用できません。  
  
-   サーバーが非同期の場合、サービスのコードを実行している間は、完全な呼び出し履歴を表示できません。  
  
-   app.config ファイルまたは Web.config ファイルの次のコードでデバッグが有効にされている必要があります。  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     このコードは一度だけ追加する必要があります。 このコードを追加するには、.config ファイルを編集するかを使用して、サービスにアタッチして**プロセスにアタッチ**します。 使用すると**プロセスにアタッチ**サービスで、デバッグ コードが自動的に .config ファイルに追加します。 その後は、.config ファイルを編集せずにサービスをデバッグし、ステップ インできます。  
  
## <a name="limitations-on-stepping-out-of-a-service"></a>サービスからのステップ アウトの制約  
 サービスからステップ アウトしてクライアントに戻る際には、サービスへのステップ インと同じ制約があります。 また、デバッガーをクライアントにアタッチする必要があります。 クライアントをデバッグし、サービスにステップ インしても、デバッガーはサービスにアタッチしたままです。 これは、true を使用してクライアントを起動するかどうか**デバッグの開始**を使用して、クライアントにアタッチされている**プロセスにアタッチ**します。 サービスにアタッチしてデバッグを開始した場合、デバッガーはまだクライアントにアタッチされていません。 その場合は、ステップ アウト、サービスとクライアントがあれば、する必要があります最初に使用する**プロセスにアタッチ**クライアントに手動でアタッチします。  
  
## <a name="limitations-on-automatic-attach-to-a-service"></a>サービスへのオート アタッチの制約  
 サービスへのオート アタッチには、次の制約があります。  
  
-   サービスは、デバッグしている [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ソリューションの一部である必要があります。  
  
-   サービスはホストされている必要があります。 サービスは、Web サイト プロジェクト (ファイル システムおよび HTTP)、Web アプリケーション プロジェクト (ファイル システムおよび HTTP)、または WCF サービス ライブラリ プロジェクトの一部にすることができます。 WCF サービス ライブラリ プロジェクトは、サービス ライブラリまたはワークフロー サービス ライブラリです。  
  
-   サービスは、WCF クライアントから起動される必要があります。  
  
-   app.config ファイルまたは Web.config ファイルの次のコードでデバッグが有効にされている必要があります。  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## <a name="self-hosting"></a>セルフホスト  
 A*自己ホスト型サービス*WCF サービス、WCF サービス ホストを IIS 内で実行していない、または[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]開発サーバーです。 自己ホスト型サービスをデバッグする方法については、次を参照してください。[方法: 自己ホスト型 WCF サービスをデバッグ](../debugger/how-to-debug-a-self-hosted-wcf-service.md)します。  
  
## <a name="self-hosting"></a>セルフホスト  
 デバッグを有効にする[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]3.0 または 3.5 アプリケーションでは、 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 3.0 または 3.5 をインストールする前にする必要がある[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]がインストールされています。 場合[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]する前にインストールされている[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]をデバッグするときにエラーが発生した 3.0 または 3.5 を[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]3.0 または 3.5 アプリケーションです。 エラー メッセージは、「サーバーに自動的にステップ インできません。」です。 この問題を解決する、Windows を使用して、**コントロール パネルの **、**プログラムと機能**を修復する、[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]インストールします。  
  
## <a name="see-also"></a>関連項目  
 [WCF サービスのデバッグ](../debugger/debugging-wcf-services.md)   
 [方法 : セルフホストされている WCF サービスをデバッグする](../debugger/how-to-debug-a-self-hosted-wcf-service.md)



