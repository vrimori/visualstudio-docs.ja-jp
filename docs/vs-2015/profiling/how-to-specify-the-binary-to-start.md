---
title: '方法: 開始するバイナリを指定する | Microsoft Docs'
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
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec65dd3a5bcc812ff2f7c42ae4cbbba6080664db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539514"
---
# <a name="how-to-specify-the-binary-to-start"></a>方法 : 開始するバイナリを指定する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: 開始するバイナリを指定](https://docs.microsoft.com/visualstudio/profiling/how-to-specify-the-binary-to-start)します。  
  
DLL などのバイナリをプロファイルするには、**[\<Target> プロパティ ページ]** ダイアログ ボックスに情報を入力する必要があります。 この情報は、DLL プロジェクトの呼び出し元アプリケーションの場所を示します。  
  
 **必要条件**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、[!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]、[!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>開始する実行可能ファイルを指定するには  
  
1.  **パフォーマンス エクスプローラー**で、対象のバイナリを右クリックし、**[プロパティ]** をクリックします。  
  
2.  **[プロパティ ページ]** ダイアログ ボックスで、**[起動]** プロパティをクリックします。  
  
3.  **[プロジェクト プロパティのオーバーライド]** チェック ボックスを選択します。  
  
4.  **[起動する実行可能ファイル]** テキスト ボックスで、ファイルの場所を指定します。  
  
5.  **[引数]** テキスト ボックスで、アプリケーションを起動するのに必要な引数を指定します。  
  
6.  **[作業ディレクトリ]** テキスト ボックスで、ディレクトリの場所を指定します。  
  
7.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)



