---
title: 'エラー: デバッグではありません&#39;Possible Because カーネル デバッガーがシステムで有効になっている t |Microsoft Docs'
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
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- kernel debugger
ms.assetid: 630a7abd-3303-4aaa-888a-6de3de14bc01
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95ee7bddb45fdcdadfdf9cce077b550509ab4c5d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47549193"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>エラー: デバッグではありません&#39;t Possible Because カーネル デバッガーがシステムで有効になっています。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[エラー: デバッグではありません&#39;t Possible Because カーネル デバッガーがシステムで有効になっている](https://docs.microsoft.com/visualstudio/debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system)します。  
  
マネージド コードのデバッグ時に、次のエラー メッセージが表示されることがあります。  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 このメッセージは次の場合にマネージド コードをデバッグしようとすると表示されます。  
  
-   [!INCLUDE[win7](../includes/win7-md.md)] または [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] システムがデバッグ モードで起動している。  
  
-   アプリケーションが CLR バージョン CLR 2.0、3.0、または 3.5 を使用している。  
  
## <a name="solution"></a>ソリューション  
  
#### <a name="to-fix-this-problem"></a>この問題を解決するには  
  
-   CLR バージョン 4.0 または 4.5 を使用するようにアプリケーションをアップグレードします。  
  
     または  
  
-   カーネル デバッグを無効にし、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] でデバッグを実行します。  
  
     または  
  
-   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の代わりにカーネル デバッガーを使用してデバッグを実行します。  
  
     または  
  
-   カーネル デバッガーで、ユーザー モード例外を無効にします。  
  
#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>現在のセッションでカーネル デバッグを無効にするには  
  
-   コマンド プロンプトで、次のコマンドを入力します。  
  
    ```  
    Kdbgctrl.exe -d  
    ```  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>すべてのセッションでカーネル デバッグを無効にするには (Windows Vista および Windows 7)  
  
1.  コマンド プロンプトで、次のコマンドを入力します。  
  
    ```  
    bcdedit /debug off   
    ```  
  
2.  コンピューターを再起動します。  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>すべてのセッションでカーネル デバッグを無効にするには (その他の Windows オペレーティング システム)  
  
1.  Boot.ini、システム ドライブを探します (通常は c:\\)。 boot.ini ファイルは、読み取り専用で非表示になっていることがあります。 この場合、次のコマンドを使用して表示する必要があります。  
  
    ```  
    dir /ASH  
    ```  
  
2.  boot.ini をメモ帳で開き、次のオプションを削除します。  
  
    ```  
    /debug  
    /debugport  
    /baudrate  
    ```  
  
3.  コンピューターを再起動します。  
  
#### <a name="to-debug-with-the-kernel-debugger"></a>カーネル デバッガーを使用してデバッグを実行するには  
  
1.  カーネル デバッガーがフックされている場合、デバッグを続行するかどうかを確認するメッセージが表示されます。 ボタンをクリックして続行します。  
  
2.  `User break exception(Int 3).` が発生することがあります。その場合は、次のカーネル デバッガー コマンドを入力してデバッグを続行します。  
  
     `gn`  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)



