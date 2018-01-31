---
title: "方法 : ホスト プロセスを無効にする | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b43e285c35601cb0d50536a5f4c499d09ae9bbad
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-disable-the-hosting-process"></a>方法 : ホスト プロセスを無効にする
ホスト プロセスが有効になっていると、特定の API の呼び出しに影響する場合があります。 影響がある場合は、正しい結果が返るようにホスト プロセスを無効にする必要があります。  
  
### <a name="to-disable-the-hosting-process"></a>ホスト プロセスを無効にするには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で、実行可能なプロジェクトを開きます。 実行可能ファイルを生成しないプロジェクト (クラス ライブラリやサービス プロジェクトなど) には、このオプションがありません。  
  
2.  **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
3.  **[デバッグ]** タブをクリックします。  
  
4.  **[Visual Studio ホスティング プロセスを有効にする]** チェック ボックスをオフにします。  
  
 ホスト プロセスが無効になると、一部のデバッグ機能が使用できなくなったり、パフォーマンスが低下したりします。 詳しくは、「[プロセスのデバッグとホスト](../debugger/debugging-and-the-hosting-process.md)」をご覧ください。  
  
 一般的に、ホスト プロセスが無効になると、次のことが起こります。  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] アプリケーションのデバッグが始まるまでの時間が長くなる。  
  
-   デザイン時の式評価が使用できなくなる。  
  
-   部分信頼デバッグが使用できなくなる。  
  
## <a name="see-also"></a>関連項目

[プロセスのデバッグとホスト](../debugger/debugging-and-the-hosting-process.md)   
[ホスト プロセス (vshost.exe)](../ide/hosting-process-vshost-exe.md)