---
title: "Office でのスレッドのサポート | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "複数のスレッド [Visual Studio での Office 開発]"
  - "オブジェクト モデル [Visual Studio での Office 開発], スレッド処理のサポート"
  - "Office アプリケーション [Visual Studio での Office 開発], スレッド処理のサポート"
  - "スレッド処理 [Visual Studio での Office 開発]"
ms.assetid: 810a6648-fece-4b43-9eb6-948d28ed2157
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Office でのスレッドのサポート
  このトピックでは、Microsoft Office オブジェクト モデルでスレッドをサポートする方法について説明します。  Office オブジェクト モデルはスレッド セーフではありませんが、Office ソリューションでは複数のスレッドを操作できます。  Office アプリケーションは、コンポーネント オブジェクト モデル \(COM: Component Object Model\) サーバーです。  COM により、クライアントは、任意のスレッド上で COM サーバーを呼び出すことができます。  スレッド セーフではない COM サーバーのために、COM には、常に 1 つの論理スレッドだけがサーバーで実行されるように同時呼び出しをシリアル化する機構が用意されています。  この機構は、シングルスレッド アパートメント \(STA: Single\-Threaded Apartment\) モデルと呼ばれます。  呼び出しがシリアル化されるため、サーバーがビジー状態の場合やバックグラウンド スレッドで他の呼び出しを処理している場合は、呼び出し元がその期間ブロックされることがあります。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 複数のスレッドを使用するときに必要な知識  
 複数のスレッドを使用するには、少なくとも、マルチスレッドの次の点に関する基本的な知識が必要です。  
  
-   Windows API  
  
-   COM マルチスレッドの概念  
  
-   Concurrency  
  
-   同期  
  
-   マーシャリング  
  
 マルチスレッドに関する一般的な情報については、「[コンポーネントのマルチスレッド](../Topic/Multithreading%20in%20Components.md)」を参照してください。  
  
 Office はメイン STA で実行されます。  これが意味するところを理解することにより、Office で複数のスレッドを使用する方法を理解できます。  
  
## 基本的なマルチスレッドのシナリオ  
 Office ソリューションのコードは、常にメイン UI スレッドで実行されます。  個々のタスクをバックグラウンド スレッドで実行して、アプリケーションのパフォーマンスを改善することが必要な場合があります。  複数のスレッドを使用する主な目的は、タスクがさらに円滑に実行されるようにすることです。そのためには、2 つのタスクが順に実行されるのではなく、2 つのタスクが一度に完了したように見える必要があります。  たとえば、Excel のメイン UI スレッドにイベント コードを配置し、バックグラウンド スレッドでは、サーバーからデータを収集してそのデータで Excel UI のセルを更新するタスクを実行するとします。  
  
## Office オブジェクト モデルを呼び出すバックグラウンド スレッド  
 バックグラウンド スレッドが Office アプリケーションを呼び出すと、呼び出しは STA 境界で自動的にマーシャリングされます。  ただし、バックグラウンド スレッドが呼び出したときに Office アプリケーションでその呼び出しを処理できるという保証はありません。  いくつかの考慮事項を次に示します。  
  
1.  Office アプリケーションは、入力の機会を得るために、その呼び出しのメッセージを調査する必要があります。  この処理が集中的に行われ、スレッドが明け渡されないと、時間がかかることがあります。  
  
2.  別の論理スレッドが既にアパートメントにある場合、新しいスレッドは入ることができません。  これは、論理スレッドが Office アプリケーションに入った後、再入可能な呼び出しを呼び出し元のアパートメントに戻す場合によく発生します。  アプリケーションは、その呼び出しが戻るのを待っている間にブロックされます。  
  
3.  Excel は、受け取った呼び出しをすぐに処理できないような状態の場合があります。  たとえば、Office アプリケーションはモーダル ダイアログを表示している場合があります。  
  
 考慮事項 2 と考慮事項 3 については、[IMessageFilter](http://msdn.microsoft.com/ja-jp/e12d48c0-5033-47a8-bdcd-e94c49857248) インターフェイスが COM に用意されています。  サーバーがこのインターフェイスを実装すると、すべての呼び出しが [HandleIncomingCall](http://msdn.microsoft.com/ja-jp/7e31b518-ef4f-4bdd-b5c7-e1b16383a5be) メソッドを介して実行されます。  考慮事項 2 では、呼び出しが自動的に拒否されます。  考慮事項 3 では、サーバーは、状況に応じて、呼び出しを拒否できます。  呼び出しが拒否された場合、呼び出し元は処理を決める必要があります。  通常、呼び出し元は、[IMessageFilter](http://msdn.microsoft.com/ja-jp/e12d48c0-5033-47a8-bdcd-e94c49857248) を実装します。この場合、[RetryRejectedCall](http://msdn.microsoft.com/ja-jp/3f800819-2a21-4e46-ad15-f9594fac1a3d) メソッドによって、拒否されたことが呼び出し元に通知されます。  
  
 ただし、Visual Studio の Office 開発ツールで作成されたソリューションの場合、COM 相互運用機能により、拒否されたすべての呼び出しが <xref:System.Runtime.InteropServices.COMException> \("メッセージ フィルターはアプリケーションがビジーであることを示しています。"\) に変換されます。  バックグラウンド スレッドでオブジェクト モデルを呼び出す場合は、この例外を処理する準備をしておく必要があります。  通常、この呼び出しでは、一定時間再試行を行ってから、ダイアログを表示します。  ただし、バックグラウンド スレッドを STA として作成してから、そのスレッドのメッセージ フィルターを登録してこのケースを処理することもできます。  
  
## スレッドの適切な起動  
 新しい STA スレッドを作成するときには、アパートメント状態を STA に設定してから、スレッドを起動する必要があります。  これを実行する方法を次のコード例に示します。  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/CS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/VB/ThisWorkbook.vb#5)]  
  
 詳細については、「[Managed Threading Best Practices](../Topic/Managed%20Threading%20Best%20Practices.md)」を参照してください。  
  
## モードレス フォーム  
 モードレス フォームでは、フォームが表示されている間にアプリケーションに対していくつかの種類の操作を行うことができます。  ユーザーはフォームとやり取りし、フォームはアプリケーションを閉じずにアプリケーションとやり取りします。  マネージ モードレス フォームは Office オブジェクト モデルでサポートされていますが、バックグラウンド スレッドでは使用しないでください。  
  
## 参照  
 [コンポーネントのマルチスレッド](../Topic/Multithreading%20in%20Components.md)   
 [Managed Threading](../Topic/Managed%20Threading.md)   
 [スレッド処理 &#40;C&#35; および Visual Basic&#41;](../Topic/Threading%20(C%23%20and%20Visual%20Basic).md)   
 [Using Threads and Threading](../Topic/Using%20Threads%20and%20Threading.md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)  
  
  