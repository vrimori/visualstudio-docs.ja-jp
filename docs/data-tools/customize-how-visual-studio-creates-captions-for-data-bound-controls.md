---
title: "方法 : Visual Studio がデータ バインド コントロールのキャプションを作成する方法をカスタマイズする | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "キャプション, データ バインド"
  - "[データ ソース] ウィンドウ, ラベル付け (キャプションの)"
  - "ラベル付け (キャプションの), [データ ソース] ウィンドウ"
  - "スマート キャプション"
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 12
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法 : Visual Studio がデータ バインド コントロールのキャプションを作成する方法をカスタマイズする
[ウィンドウ](../Topic/Data%20Sources%20Window.md)から Windows フォーム デザイナーに項目をドラッグする場合は、特別な配慮が必要です。複数の単語が連結されているキャプション ラベルの列名は、より判読しやすい文字列に再編成されます。  このラベルの作成方法は、**HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\10.0\\Data Designers** レジストリ キーの **SmartCaptionExpression** 値、**SmartCaptionReplacement** 値、および **SmartCaptionSuffix** 値を設定することによってカスタマイズできます。  
  
> [!NOTE]
>  このレジストリ キーは存在しないので、作成する必要があります。  
  
 スマート キャプションは、**SmartCaptionExpression** 値に入力される正規表現によって制御されます。  **Data Designers** レジストリ キーを追加すると、キャプション ラベルを制御する既定の正規表現がオーバーライドされます。  正規表現の詳細については、「[Visual Studio での正規表現の使用](../ide/using-regular-expressions-in-visual-studio.md)」を参照してください。  
  
 キャプション ラベルを制御するレジストリ値の説明を次の表に示します。  
  
|レジストリ項目|Description|  
|-------------|-----------------|  
|SmartCaptionExpression|目的のパターンに対応する正規表現です。|  
|SmartCaptionReplacement|**SmartCaptionExpression** に対応するグループの表示書式です。|  
|SmartCaptionSuffix|キャプションの最後に追加する文字列です \(省略可能\)。|  
  
 これらのレジストリ値の内部的な既定の設定の一覧を次の表に示します。  
  
|項目|既定値|説明|  
|--------|---------|--------|  
|**SmartCaptionExpression**|\(\\\\p{Ll}\)\(\\\\p{Lu}\)&#124;\_\+|小文字の後に大文字またはアンダースコアが続くパターンに一致します。|  
|**SmartCaptionReplacement**|$1 $2|$1 は正規表現の最初のかっこ内の文字列表現を表し、$2 は 2 番目のかっこ内の文字列表現を表します。  置換後の表現は、最初の一致候補、スペース、そして 2 番目の一致候補です。|  
|**SmartCaptionSuffix**|:|返す文字列に追加する文字を表します。  たとえば、`Company Name` というキャプションは、このサフィックスによって `Company Name:` になります。|  
  
> [!CAUTION]
>  レジストリ エディターで作業する場合は、細心の注意を払う必要があります。  レジストリを編集する前にバックアップを作成してください。  レジストリ エディターで不適切な操作を行うと、重大な問題が発生して、オペレーティング システムの再インストールが必要になる場合もあります。  マイクロソフトは、レジストリ エディターの不適切な使用によって発生した問題の解決は保証できません。  問題が発生する可能性のあることを十分に認識したうえで利用してください。  
>   
>  レジストリのバックアップ、編集、および復元の方法については、サポート技術情報の「[上級ユーザー向けの Windows レジストリ情報](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986)」\(http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;256986\) を参照してください。  
  
### \[データ ソース\] ウィンドウのスマート キャプションの動作を変更するには  
  
1.  **\[スタート\]** ボタンをクリックし、**\[ファイル名を指定して実行\]** をクリックしてコマンド ウィンドウを開きます。  
  
2.  **\[ファイル名を指定して実行\]** ダイアログ ボックスで、「`regedit`」と入力して **\[OK\]** をクリックします。  
  
3.  **HKEY\_CURRENT\_USER** ノードを展開します。  
  
4.  **Software** ノードを展開します。  
  
5.  **Microsoft** ノードを展開します。  
  
6.  **VisualStudio** ノードを展開します。  
  
7.  **10.0** ノードを右クリックし、「`Data Designers`」という **\[キー\]** を新規作成します。  
  
8.  **Data Designers** ノードを右クリックし、「`SmartCaptionExpression`」という **\[文字列値\]** を新規作成します。  
  
9. **Data Designers** ノードを右クリックし、「`SmartCaptionReplacement`」という **\[文字列値\]** を新規作成します。  
  
10. **Data Designers** ノードを右クリックし、「`SmartCaptionSuffix`」という **\[文字列値\]** を新規作成します。  
  
11. **\[SmartCaptionExpression\]** 項目を右クリックし、**\[修正\]** をクリックします。  
  
12. **\[データ ソース\]** ウィンドウが使用する正規表現を入力します。  
  
13. **\[SmartCaptionReplacement\]** 項目を右クリックし、**\[修正\]** をクリックします。  
  
14. 正規表現に対応する表示パターンによって書式設定した置換文字列を入力します。  
  
15. **\[SmartCaptionSuffix\]** 項目を右クリックし、**\[修正\]** をクリックします。  
  
16. キャプションの最後に表示する文字列を入力します。  
  
     次回、**\[データ ソース\]** ウィンドウから項目をドラッグすると、指定した新しいレジストリを使用してキャプション ラベルが作成されます。  
  
### スマート キャプション機能をオフにするには  
  
1.  **\[スタート\]** ボタンをクリックし、**\[ファイル名を指定して実行\]** をクリックしてコマンド ウィンドウを開きます。  
  
2.  **\[ファイル名を指定して実行\]** ダイアログ ボックスで、「`regedit`」と入力して **\[OK\]** をクリックします。  
  
3.  **HKEY\_CURRENT\_USER** ノードを展開します。  
  
4.  **Software** ノードを展開します。  
  
5.  **Microsoft** ノードを展開します。  
  
6.  **VisualStudio** ノードを展開します。  
  
7.  **10.0** ノードを右クリックし、「`Data Designers`」という **\[キー\]** を新規作成します。  
  
8.  **Data Designers** ノードを右クリックし、「`SmartCaptionExpression`」という **\[文字列値\]** を新規作成します。  
  
9. **Data Designers** ノードを右クリックし、「`SmartCaptionReplacement`」という **\[文字列値\]** を新規作成します。  
  
10. **Data Designers** ノードを右クリックし、「`SmartCaptionSuffix`」という **\[文字列値\]** を新規作成します。  
  
11. **\[SmartCaptionExpression\]** 項目を右クリックし、**\[修正\]** をクリックします。  
  
12. 値として「`(.*)`」を入力します。  これは、文字列全体に対応します。  
  
13. **\[SmartCaptionReplacement\]** 項目を右クリックし、**\[修正\]** をクリックします。  
  
14. 値として「`$1`」を入力します。  これによって、文字列は一致した値で置き換えられます。この場合は、文字列全体になるので変更はありません。  
  
     次回、**\[データ ソース\]** ウィンドウから項目をドラッグすると、キャプション ラベルは変更されずに作成されます。  
  
## 参照  
 [.NET Framework の正規表現](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)