---
title: "方法 : ClickOnce アプリケーションの既定の Web ページをカスタマイズする | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Publish.htm Web ページ"
  - "ClickOnce 配置の既定の Web ページ"
  - "アプリケーションの配置 [ClickOnce]、発行"
  - "発行、ClickOnce"
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : ClickOnce アプリケーションの既定の Web ページをカスタマイズする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce アプリケーションを Web に発行するとき、Web ページが自動的に生成され、アプリケーションと共に発行されます。  既定のページには、アプリケーションの名前に加えて、アプリケーションのインストール、必須コンポーネントのインストール、または MSDN のヘルプへのアクセスを実行するためのリンクが表示されます。  
  
> [!NOTE]
>  実際にページに表示されるリンクは、ページを表示するコンピューターと、必須コンポーネントの内容によって異なります。  
  
 Web ページの既定の名前は Publish.htm ですが、**プロジェクト デザイナー**で名前を変更できます。  詳細については、「[方法 : ClickOnce アプリケーションの発行ページを指定する](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)」を参照してください。  
  
 Publish.htm Web ページは、より新しいバージョンが検出されない場合にのみ発行されます。  
  
> [!NOTE]
>  **\[発行\]** の設定を変更しても、Publish.htm ページには影響を及ぼしません。ただし例外として、最初に発行した後で必須コンポーネントを追加または削除した場合は、必須コンポーネントの一覧が正しくなくなります。  必須コンポーネントへのリンクのテキストを編集して、変更を反映する必要があります。  
  
### 発行 Web ページをカスタマイズするには  
  
1.  ClickOnce アプリケーションを Web 上の場所に発行します。  詳細については、「[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)」を参照してください。  
  
2.  Web サーバー上で、Visual Web Designer か他の HTML エディターで Publish.htm ファイルを開きます。  
  
3.  必要に応じてページをカスタマイズし、保存します。  
  
4.  省略可能。  カスタマイズした発行 Web ページが Visual Studio で上書きされないようにするには、\[発行オプション\] ダイアログ ボックスの **\[発行後に毎回配置 Web ページを自動的に生成する\]** チェック ボックスをオフにします。  
  
## 参照  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法 : ClickOnce アプリケーションと共に必須コンポーネントをインストールする](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [方法 : ClickOnce アプリケーションの発行ページを指定する](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)