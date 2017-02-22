---
title: "プロファイルと Windows Vista のセキュリティ | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロファイル ツール、セキュリティ"
  - "パフォーマンス ツール、セキュリティ"
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# プロファイルと Windows Vista のセキュリティ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コンピューター管理者が行った [!INCLUDE[wiprlhext](../misc/includes/wiprlhext_md.md)] ユーザーのアクセス許可の設定に応じて、ユーザーごとに、そのコンピューター上でプロセスのプロファイリングを行うためのセキュリティ アクセス許可が付与されている場合があります。  ユーザー間での予測される相違点の例は次のとおりです。  
  
-   一部のユーザーは、高度なプロファイル機能にアクセスできます \(管理者がドライバーやサービスの開始について設定を行った場合\)。  
  
-   ドメイン ユーザーは、サンプル プロファイルのみにアクセスできることがあります。  
  
-   一部のユーザーは、他のすべてのユーザーのプロファイルへのアクセスを拒否されることがあります。  
  
 詳細については、「[VSPerfCmd](../profiling/vsperfcmd.md)」の ADMIN オプションに関する説明を参照してください。  
  
## セッション間プロファイリング  
 *セッション間プロファイリング*は、異なるログオン セッションで実行されるプロセスのプロファイリングを実行する機能です。  たとえば、サービスのほとんどはセッション 0 で実行されますが、ユーザーはセッション 0 で直接実行することができません。  パフォーマンス エクスプローラー ツール バーの **\[プロセスにアタッチ\]** ボタンを使用するか、または VSPerfCmd コマンド ライン ツールの \/attach オプションを使用すると、異なるログオン セッションのほとんどのプロセスを実行することができます。  
  
 プロセス間プロファイリングの可視性に関するオプションを設定することで、使用できるプロセスの一覧を参照できます。  **\[プロセスにアタッチ\]** をクリックすると表示される **\[プロセスにアタッチ\]** ウィンドウで以下のオプションを選択できます。  
  
-   **\[すべてのユーザーからのプロセスを表示する\]**  
  
     このオプションを選択しないと、現在のユーザーが所有するプロセスだけの一覧が表示されます。  **\[すべてのユーザーからのプロセスを表示する\]** を選択すると、すべてのユーザーからのプロセスの一覧が表示されます。  
  
-   **\[すべてのセッションのプロセスを表示する\]**  
  
     このオプションを選択しないと、現在のセッションにあるプロセスの一覧が表示されます。  オプションを選択すると、すべてのセッションにあるプロセスの一覧が表示されます。  
  
## 参照  
 [概要](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [How to: Attach to a Running Process](http://msdn.microsoft.com/ja-jp/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)