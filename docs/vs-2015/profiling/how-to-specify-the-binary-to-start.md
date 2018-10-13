---
title: '方法: 開始するバイナリを指定する | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 95539f978121dd5fb366776321498d33ac1ee92a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194338"
---
# <a name="how-to-specify-the-binary-to-start"></a>方法 : 開始するバイナリを指定する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DLL などのバイナリをプロファイルするには、**[\<Target> プロパティ ページ]** ダイアログ ボックスに情報を入力する必要があります。 この情報は、DLL プロジェクトの呼び出し元アプリケーションの場所を示します。  
  
 **必要条件**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]、 [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
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



