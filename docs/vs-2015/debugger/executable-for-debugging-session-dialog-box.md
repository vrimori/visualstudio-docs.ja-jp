---
title: デバッグ セッション ダイアログ ボックスの実行可能ファイル |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31190bf669d11929aed8127d8433d86c8fc75c4b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535946"
---
# <a name="executable-for-debugging-session-dialog-box"></a>[デバッグ セッションで実行可能] ダイアログ ボックス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[デバッグ セッション ダイアログ ボックスの実行可能ファイル](https://docs.microsoft.com/visualstudio/debugger/executable-for-debugging-session-dialog-box)します。  
  
このダイアログ ボックスは、ダイナミック リンク ライブラリ (DLL: Dynamic-Link Library) をデバッグするときに、実行可能ファイルが指定されていない場合に表示されます。 Visual Studio では、DLL を直接起動できません。 代わりに、指定した実行可能ファイルが起動されます。 DLL は、実行可能ファイルから呼び出されたときにデバッグできます。  
  
 **実行可能ファイル名**  
 デバッグ中の DLL を呼び出す実行可能ファイルへのパス名を入力します。  
  
 **プロジェクトにアクセスする URL (ATL Server のみ)**  
 ATL Server の DLL をデバッグする場合は、プロジェクトが存在する URL を入力します。  
  
 URL を入力すると、これらの設定がプロジェクトの [プロパティ ページ] に格納されるため、後続のデバッグ セッションで設定を再入力する必要がなくなります。 設定変更が必要な場合は [プロパティ ページ] を開いて値を変更できます。 デバッグ セッションで、実行可能ファイルを指定する方法の詳細については、次を参照してください。 [Dll のデバッグ](../debugger/how-to-debug-native-dlls.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)



