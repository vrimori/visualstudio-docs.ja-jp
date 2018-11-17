---
title: Web コントロール ライブラリ (マネージ コード) |Microsoft Docs
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
- debugging DLLs
- debugging [Visual Studio], Web control libraries
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a523d593b4c61a7ca730cc60a6ed22a1be541f9c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807596"
---
# <a name="web-control-library-managed-code"></a>Web コントロール ライブラリ (マネージド コード)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Web コントロール ライブラリ プロジェクト テンプレートは DLL を作成します。 クラス ライブラリは DLL であるため、直接実行することはできません。 コントロールを埋め込む [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ページを作成する必要があります。 詳細については、次を参照してください。 [Web コントロール ライブラリ テンプレート](http://msdn.microsoft.com/en-us/00666b07-71d2-4ace-a13c-cc130a3ce372)します。  
  
### <a name="to-debug-a-web-control-library-method-1"></a>Web コントロール ライブラリをデバッグするには (方法 1)  
  
1.  既存の Web コントロール ライブラリ プロジェクトを開くか、新しいプロジェクトを作成します。  
  
2.  コントロールを埋め込む [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ページを作成します。  
  
3.  [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] テスト ハーネスをホストしている Web サイトで、`/Code` という名前のサブディレクトリを作成します。  
  
4.  コントロールのソース コードを `/Code` サブディレクトリにコピーします。  
  
5.  `/Code` サブディレクトリでソース コードを開き、ブレークポイントを設定します。  
  
6.  テスト ハーネスを指す URL を使用してブラウザー ウィンドウを開きます。 コントロール内のブレークポイントにヒットすると、デバッグを開始できます。  
  
### <a name="to-debug-a-web-control-library-method-2"></a>Web コントロール ライブラリ (メソッドの 2) をデバッグするには  
  
1.  ホスト アプリケーション プロジェクトと Web コントロール プロジェクトを同じソリューションで作成します。  
  
2.  **ソリューション エクスプ ローラー**をホスト アプリケーションを右クリックして**参照の追加**します。  
  
3.  Web コントロール プロジェクトへの参照を追加します。  
  
## <a name="see-also"></a>関連項目  
 [ASP.NET Web アプリケーション](../debugger/debugging-preparation-aspnet-web-applications.md)



