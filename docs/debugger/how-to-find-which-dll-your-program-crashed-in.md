---
title: "方法 : プログラムのクラッシュが発生している DLL を確認する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.dll"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "デバッガー, DLL クラッシュ"
  - "デバッグ [Visual Studio], DLL クラッシュ"
  - "DLL, 読み込み順序"
  - "エラー [デバッガー], DLL クラッシュ"
  - "モジュール一覧のダイアログ ボックス"
  - "[モジュール] ウィンドウ"
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : プログラムのクラッシュが発生している DLL を確認する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、\[ツール\] メニューの \[設定のインポートとエクスポート\] をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 システム DLL または他の開発者が作成したコードを呼び出す部分でアプリケーションがクラッシュした場合、クラッシュが発生した DLL を確認する必要があります。  プログラム外の DLL でクラッシュが発生している場合は、**\[モジュール\]** ウィンドウを使用してその場所を確認できます。  
  
### \[モジュール\] ウィンドウを使ってクラッシュの発生場所を確認するには  
  
1.  クラッシュが発生したアドレスをメモします。  
  
2.  **\[デバッグ\]** メニューの **\[ウィンドウ\]** をポイントし、**\[モジュール\]** をクリックします。  
  
3.  **\[モジュール\]** ウィンドウの **\[アドレス\]** 列に注目します。  必要に応じて、スクロール バーを使用します。  
  
4.  列の上部にある **\[アドレス\]** ボタンをクリックして、DLL をアドレス順に並べ替えます。  
  
5.  並べ替えたリストを検索して、アドレス範囲内にクラッシュ場所がある DLL を探します。  
  
6.  **\[名前\]** 列と **\[パス\]** 列で、DLL の名前とパスを確認します。  
  
## 参照  
 [方法: ネイティブ DLL サーバーをデバッグする](../Topic/How%20to:%20Debug%20Native%20DLLs.md)   
 [方法 : \[モジュール\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Modules%20Window.md)