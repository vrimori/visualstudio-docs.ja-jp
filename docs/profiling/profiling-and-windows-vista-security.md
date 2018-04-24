---
title: プロファイルと Windows Vista のセキュリティ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f03c5d6a7afec1010653c6e4a66a3770573ea5e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="profiling-and-windows-vista-security"></a>プロファイルと Windows Vista のセキュリティ
コンピューターの管理者が使用可能にした [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] ユーザー アクセス許可の設定に応じて、個々のユーザーは、コンピューター上でプロセスをプロファイリングするためのセキュリティ アクセス許可を持っている場合があります。 次の例では、考えられるユーザーごとの違いについて説明します。  
  
-   管理者がドライバーとサービスが起動するように設定しているときには、一部のユーザーが高度なプロファイリング機能にアクセスできることがあります。  
  
-   ドメイン ユーザーはサンプルのプロファイリングにのみアクセスできる場合があります。  
  
-   一部のユーザーが他のすべてのユーザーに対してプロファイリングへのアクセスを拒否することがあります。  
  
 詳細については、「[VSPerfCmd](../profiling/vsperfcmd.md)」の ADMIN オプションを参照してください。  
  
## <a name="cross-session-profiling"></a>セッション間プロファイリング  
 *セッション間プロファイリング*は、別のログオン セッションで実行しているプロセスをプロファイリングする機能です。 たとえば、サービスのほとんどはセッション 0 で実行され、ユーザーはセッション 0 で直接実行できません。 パフォーマンス エクスプローラーのツールバーで **[プロセスにアタッチ]** ボタン、または VSPerfCmd コマンド ライン ツールの /attach オプションを使用して、さまざまなログオン セッションでのほとんどのプロセスをプロファイリングすることができます。  
  
 プロセス間のプロファイルの表示オプションを設定すると、使用できるプロセスの一覧が表示できます。 これらのオプションは、**[プロセスにアタッチ]** をクリックすると表示される **[プロセスにアタッチ]** ウィンドウで利用できます。  
  
-   **全ユーザーのプロセスを表示する**  
  
     このオプションを選択していない場合、一覧には、現在のユーザーによって所有されているプロセスのみが表示されます。 **[全ユーザーのプロセスを表示する]** を選択すると、一覧には、すべてのユーザーのプロセスが表示されます。  
  
-   **すべてのセッションのプロセスを表示**  
  
     このオプションを選択していない場合、一覧には、現在のセッションのプロセスが表示されます。 このオプションを選択すると、一覧には、すべてのセッションのプロセスが表示されます。  
  
## <a name="see-also"></a>参照  
 [概要](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [方法: 実行中のプロセスにアタッチする](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)