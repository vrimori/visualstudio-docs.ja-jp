---
title: '方法: インストルメンテーションを特定の関数に制限する | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f06408b65d3cda1f2ee807daac7ab39ce2182a90
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891780"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>方法 : インストルメンテーションを特定の関数に制限する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

インストルメンテーションとデータ収集は、1 つ以上の関数に制限することができます。これを行うには、**[パフォーマンス セッション]** のプロパティ ページまたはターゲット バイナリのプロパティ ページの **[詳細]** ページでオプションを設定します。  
  
- パフォーマンス セッションのプロパティ ページで関数を指定する場合は、セッション内のすべてのインストルメント化されたバイナリ内で、それらの関数のみがインストルメント化されます。  
  
- ターゲット バイナリのプロパティ ページで関数を指定する場合は、その特定のバイナリ内のそれらの関数のみがインストルメント化されます。 パフォーマンスの他のバイナリ内の関数は、通常どおりにインストルメント化されます。  
  
  このような方法でデータ収集を制限できるのは、インストルメンテーション プロファイル方式が選択されている場合のみです。  
  
> [!NOTE]
>  **[パフォーマンス セッション]** プロパティ ページの **[詳細]** ページで、プロファイリング ツール [VSInstr](../profiling/vsinstr.md) コマンド ライン インストルメンテーション ツールで使える他のオプションを設定することもできます。  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>インストルメンテーションをパフォーマンス セッション内の特定の関数に制限するには  
  
1. **パフォーマンス エクスプローラー**で、セッション名を右クリックして **[プロパティ]** をクリックします。  
  
    **[プロパティ ページ]** ダイアログ ボックスが表示されます。  
  
2. **[プロパティ ページ]** ダイアログ ボックスで、**[詳細]** をクリックします。  
  
3. **[追加インストルメンテーション オプション]** テキスト ボックスに、次の構文を使用して、インストルメント化する関数の名前を入力します。  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` は、名前空間と関数の名前です。 その形式は `Namespace`**::**`FunctionName` です。 複数の関数は、セミコロン (;) を使用して区切ります。 1 つまたは複数の文字にワイルドカードを指定する場合は、アスタリスク (\*) を使います。 たとえば、 **/include: MyNS::\\*** MyNS 名前空間のすべての関数を指定します。  
  
   > [!NOTE]
   >  バイナリ内の関数を一覧表示するには、プロファイリング ツールのインストール ディレクトリ (通常は、[!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]インストール ディレクトリの下にある \Team Tools\Performance Tools ディレクトリ) でコマンド プロンプト ウィンドウを開き、**vsinstr /DumpFuncs** と入力します。  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>インストルメンテーションをバイナリ内の特定の関数に制限するには  
  
1. **パフォーマンス エクスプローラー**で、パフォーマンス セッションの **[ターゲット]** ノードでバイナリ名を探します。  
  
2. バイナリ名を右クリックして、**[プロパティ]** をクリックします。  
  
    **[プロパティ ページ]** ダイアログ ボックスが表示されます。  
  
3. **[プロパティ ページ]** ダイアログ ボックスで、**[詳細]** をクリックします。  
  
4. **[追加インストルメンテーション オプション]** テキスト ボックスに、次の構文を使用して、インストルメント化する関数の名前を入力します。  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` は、名前空間と関数の名前です。 その形式は `Namespace`**::**`FunctionName` です。 複数の関数は、セミコロン (;) を使用して区切ります。 1 つまたは複数の文字にワイルドカードを指定する場合は、アスタリスク (\*) を使います。 たとえば、 **/include: MyNS::\\*** MyNS 名前空間のすべての関数を指定します。  
  
   > [!NOTE]
   >  バイナリ内の関数を一覧表示するには、プロファイリング ツールのインストール ディレクトリ (通常は、[!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]インストール ディレクトリの下にある \Team Tools\Performance Tools ディレクトリ) でコマンド プロンプト ウィンドウを開き、**vsinstr /DumpFuncs** と入力します。  
  
## <a name="see-also"></a>関連項目  
 [データ コレクションの制御](../profiling/controlling-data-collection.md)   
 [方法: インストルメンテーションを特定の DLL に制限する](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [方法: 追加インストルメンテーション オプションを指定する](../profiling/how-to-specify-additional-instrumentation-options.md)



