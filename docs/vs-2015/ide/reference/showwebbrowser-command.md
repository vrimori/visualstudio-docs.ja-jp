---
title: ShowWebBrowser コマンド | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f9bf9668a690347988e3148cf90da69ec3b33ca2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49171952"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
指定した URL を統合開発環境 (IDE: Integrated Development Environment) の内部または外部の Web ブラウザーのウィンドウに表示します。  
  
## <a name="syntax"></a>構文  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## <a name="arguments"></a>引数  
 `URL`  
 必須。 Web サイトの URL (Uniform Resource Locator)。  
  
## <a name="switches"></a>スイッチ  
 /new  
 任意。 Web ブラウザーの新しいインスタンスにページが表示されるように指定します。  
  
 /ext  
 任意。 IDE の外部にある既定の Web ブラウザーにページが表示されるように指定します。  
  
## <a name="remarks"></a>Remarks  
 **ShowWebBrowser** コマンドのエイリアスは **navigate** または **nav** です。  
  
## <a name="example"></a>例  
 次の例では、IDE の外部にある Web ブラウザーに MSDN Online のホーム ページを表示します。 既に Web ブラウザーのページが開いている場合は、そのページを使用します。それ以外の場合は、新しいインスタンスが起動します。  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



