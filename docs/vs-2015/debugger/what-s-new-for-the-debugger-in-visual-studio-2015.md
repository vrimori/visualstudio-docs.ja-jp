---
title: Visual Studio 2015 のデバッガーの新機能については |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
caps.latest.revision: 86
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b7a854e872a7739054379b1f6d01794f142f448
ms.sourcegitcommit: aea5cdb76fbc7eb31d1e5cc3c8d6adb0c743220f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "47593126"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2015"></a>Visual Studio 2015 のデバッガーの新機能
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[デバッガーの新](https://docs.microsoft.com/visualstudio/debugger/what-s-new-for-the-debugger-in-visual-studio)します。  
  
Visual Studio 2015 Update 1 のデバッグと診断の新機能については、 [Visual Studio 2015 Update 1 のリリース ノート](https://www.visualstudio.com/news/vs2015-update1-vs#debug)を参照してください。  
  
 Visual Studio 2015 RTM のデバッグと診断の新機能については、 [Visual Studio 2015 のリリース ノート](https://www.visualstudio.com/news/vs2015-vs#debug)を参照してください。  
  
## <a name="visual-studio-2015-update-1-changes"></a>Visual Studio 2015 Update 1 の変更内容  
 C++ のエディット コンティニュでは、より多くの機能がサポートされています。 詳細については、次を参照してください。[エディット コンティニュ (Visual c)](../debugger/edit-and-continue-visual-cpp.md)します。  
  
 Visual C++ アクセス違反をデバッグする場合は、新しい例外ダイアログで、例外を引き起こしたポインターを指定します。 詳細についてを参照してください[アクセス違反をデバッグする方法でしょうか](../debugger/how-can-i-debug-an-access-violation-q.md)と[Visual Studio 2015 Update 1 で Debugging c Access Violations の改善。](http://blogs.msdn.com/b/visualstudioalm/archive/2015/10/29/improvement-to-debugging-c-access-violations-in-visual-studio-2015-update-1.aspx)  
  
## <a name="visual-studio-2015-rtm-debugger-ui-and-hotkey-changes"></a>Visual Studio 2015 RTM デバッガーの UI とホットキーの変更内容  
 例外とブレークポイントには、UI の重要な変更があります。  
  
### <a name="breakpoints"></a>ブレークポイント  
 Visual Studio 2015 には、 **[ブレークポイントの設定]** ウィンドウという新しいブレークポイントの構成機能があります。  
  
 ここでは、主な [ブレークポイント] ウィンドウとホットキーの概要について説明します。  
  
|機能|メニューの場所|ホット キー|  
|-------------|-------------------|------------|  
|ブレークポイントの作成、ブレークポイントの切り替え|**デバッグ/ブレークポイントの切り替え**<br /><br /> エディターのコンテキスト メニュー / **ブレークポイントの挿入**<br /><br /> 左の余白をクリック|F9|  
|新しい関数のブレークポイント|**デバッグ/新しいブレークポイント、関数のブレークポイント**|Visual Studio 2015 RTM (更新はありません) でを使用して、ALT + F9、B<br /><br /> Visual Studio 2015 Update 1 以降では、ctrl キーを押しながら B を使用します。|  
|**[ブレークポイント]** ウィンドウ|**デバッグ/Windows/ブレークポイント**|Ctrl + Alt + B|  
|**[ブレークポイント設定]**、 **[条件]**|ブレークポイントのコンテキスト メニュー / **[条件]**|Alt + F9、C|  
|**[ブレークポイント設定]**、 **[アクション]**|ブレークポイントのコンテキスト メニュー / **[アクション]**|ホットキーはありません|  
  
 詳細については、次の記事を参照してください。  
  
1.  [ブレークポイントの使用](../debugger/using-breakpoints.md)  
  
2.  [New Breakpoint Configuration Experience](http://blogs.msdn.com/b/visualstudioalm/archive/2014/10/06/new-breakpoint-configuration-experience.aspx)  
  
3.  [ブレークポイントの構成方法](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711)  
  
### <a name="exception-settings"></a>例外設定  
 新しい **[例外設定]** ウィンドウを使用すると、単一の例外または例外のカテゴリで処理する例外の種類を指定できます。  
  
|機能|メニューの場所|ホット キー|  
|-------------|-------------------|------------|  
|**[例外設定]** ウィンドウ|**デバッグ/Windows/例外設定**|Ctrl + Alt + E|  
  
 詳細については、次の記事を参照してください。  
  
1.  [デバッガーでの例外の管理](../debugger/managing-exceptions-with-the-debugger.md)  
  
2.  [新しい [例外] ウィンドウ](http://blogs.msdn.com/b/visualstudioalm/archive/2015/02/23/the-new-exception-settings-window-in-visual-studio-2015.aspx)  
  
### <a name="edit-and-continue"></a>エディット コンティニュ  
 Visual Studio 2015 の **[ツール] / [デバッグ] / [全般]** ページでエディット コンティニュを設定できます。 以前のバージョンでは、エディット コンティニュの設定はそれぞれ別のオプションのカテゴリでした。  
  
### <a name="attach-to-process"></a>プロセスにアタッチ  
 Visual Studio 2015 の [プロセスにアタッチ] コマンドは、[デバッグ] メニューからのみ使用できます。 以前のバージョンでは、[ツール] メニューからも使用できました。 Ctrl + Alt + P キー ホットキーは、すべてのバージョンで機能します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)



