---
title: '方法: 部分信頼アプリケーションのデバッグ |Microsoft Docs'
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
- debugging [Visual Studio], partial trust applications
- partial trust applications
- security [Visual Studio], partial trust applications
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6b3b7bb7e880b30e975770ee35dfb537e62827b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288224"
---
# <a name="how-to-debug-a-partial-trust-application"></a>方法 : 部分信頼アプリケーションをデバッグする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows アプリケーションとコンソール アプリケーションに適用されます。  
  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)を活用する部分信頼アプリケーションを展開しやすい[コード アクセス セキュリティ](http://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127)コンピューター上のリソースへのアクセスを制限します。  
  
 部分信頼アプリケーションのデバッグ作業は難しい場合があります。これは、部分的に信頼されたアプリケーションはインストール元によってセキュリティ アクセス許可が異なり、その結果として異なる動作をするためです。 インターネットからインストールした場合、部分信頼アプリケーションのアクセス許可は非常に制限されます。 また、ローカル イントラネットからインストールした場合はより多くのアクセス許可を持ち、ローカル コンピューターからインストールした場合はフル アクセス許可を持ちます  (カスタム アクセス許可を持つカスタム ゾーンを使用することもできます)。 場合によっては、これらのすべての条件または一部を満たして部分信頼アプリケーションをデバッグする必要があります。 Visual Studio では、これを簡単に行うことができます。  
  
 Visual Studio でデバッグ セッションを開始する前に、アプリケーションのインストール元をシミュレートするゾーンを選択できます。 デバッグを開始すると、アプリケーションは、そのゾーンからインストールされた部分信頼アプリケーションに適したアクセス許可を持ちます。 これによって、そのゾーンからアプリケーションをダウンロードするユーザーに対するアプリケーションの動作を確認できます。  
  
 アクセス許可を持たないアクションをアプリケーションが実行すると、例外が発生します。 その場合、Exception Assistant を使用してアクセス許可を追加すると、問題を回避するための十分なアクセス許可を使用してデバッグ セッションを再開できます。  
  
 デバッグ時に追加したアクセス許可は、後で確認できます。 デバッグ時にアクセス許可を追加する必要があった場合は、コードのその位置にユーザーの同意を求めるプロンプトを追加する必要があります。  
  
> [!NOTE]
>  デバッガー ビジュアライザーでは、部分信頼アプリケーションが許可する以上の特権が必要です。 部分信頼コードで動作が停止した場合、ビジュアライザーは読み込まれません。 ビジュアライザーを使用してデバッグするには、完全信頼コードを実行する必要があります。  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>部分的に信頼されたアプリケーションのゾーンを選択するには  
  
1.  **プロジェクト**] メニューの [選択_Projectname_**プロパティ**します。  
  
2.  *Projectname*プロパティ ページ をクリックして、**セキュリティ**ページ。  
  
3.  選択**ClickOnce のセキュリティ設定を有効にする**します。  
  
4.  **、アプリケーションのインストール元のゾーン**をドロップダウン リスト ボックスをクリックし、アプリケーションのインストール元をシミュレートするゾーンを選択します。  
  
     **アプリケーションで必要なアクセス許可**グリッドには、すべてのアクセス許可が表示されます。 チェック マークは、アプリケーションに与えられているアクセス許可を示します。  
  
5.  ゾーンを選択した場合 **(カスタム)**、正しいカスタム設定を選択、**設定**の列、**権限**グリッド。  
  
6.  **[OK]** をクリックし、プロパティ ページを閉じます。  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>セキュリティ例外の発生時にアクセス許可を追加するには  
  
1.  **例外処理アシスタント**メッセージ ダイアログ ボックスが表示されます: **SecurityException はハンドルされませんでした。**  
  
2.  **例外処理アシスタント**ダイアログ ボックスで、**アクション**、 をクリックして**プロジェクトへのアクセス許可を追加**します。  
  
3.  **デバッグの再開** ダイアログ ボックスが表示されます。  
  
    -   新しいアクセス許可を持つデバッグ セッションを再開する場合は、クリックして**はい**します。  
  
    -   再起動がまだない場合は、クリックして**いいえ**します。  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>デバッグ時に追加したアクセス許可を表示するには  
  
1.  **プロジェクト**] メニューの [選択_Projectname_**プロパティ**します。  
  
2.  *Projectname*プロパティ ページ をクリックして、**セキュリティ**ページ。  
  
3.  見て、**アプリケーションで必要なアクセス許可**グリッド。 追加したアクセス許可が、2 つのアイコン、**含まれている**列: が含まれるすべてのアクセス許可があるは、通常のチェック マークと文字"i"を含むバルーンのような追加アイコン。  
  
4.  垂直スクロール バーを使用して全体を表示**アプリケーションで必要なアクセス許可**グリッド。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)



