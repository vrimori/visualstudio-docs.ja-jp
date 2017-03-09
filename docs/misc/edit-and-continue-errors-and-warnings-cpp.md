---
title: "エディット コンティニュのエラーと警告 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ENC2001"
  - "ENC1006"
  - "ENC2008"
  - "ENC1009"
  - "ENC1002"
  - "ENC2002"
  - "ENC1011"
  - "ENC1003"
  - "ENC1004"
  - "ENC1008"
  - "ENC1013"
  - "ENC2005"
  - "ENC1010"
  - "ENC2004"
  - "ENC1007"
  - "ENC1005"
  - "ENC2006"
  - "ENC1001"
  - "ENC2007"
  - "ENC2003"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "エディット コンティニュ [C++], エラーと警告"
  - "エラー [C++], エディット コンティニュ"
  - "エラー [デバッガー], エディット コンティニュ"
ms.assetid: b5c5e25c-7ca4-4ca9-b91e-e8882de44dae
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "susanno"
manager: "douge"
---
# エディット コンティニュのエラーと警告 (C++)
[!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)] エディット コンティニュでは、プログラムの実行を中断モードで停止し、実行中のコードに変更を加えた後、変更結果を反映してプログラムを再開できます。  
  
 通常、クラスのパブリック構造体に影響を及ぼす宣言コードの編集は禁止されています。また、クラス内のメソッド、プロパティ本体、プライベート宣言に対する一部の編集も禁止されています。  可能な場合、エディット コンティニュで編集できないコードは明るい灰色で示され、エラー メッセージが表示されます。  [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)] のエディット コンティニュでサポートされていない編集の詳細については、「[エディット コンティニュ \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md)」を参照してください。  
  
 エディット コンティニュのエラーと警告は、次のいずれかの方法で解決できます。  
  
|解決策|エラーと警告のメッセージ番号|  
|---------|--------------------|  
|デバッグを停止して変更を再適用した後、デバッグを再開します。|1001、1002、1003、1004、1005、1006、1007、1008、1010、1013、2003、2005。このカテゴリのエラー メッセージと警告メッセージの一覧については、「[デバッグを再起動するメッセージ](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_RestartDebuggingMessages)」を参照してください。|  
|**\[編集\]** メニューの **\[元に戻す\]** をクリックし、コードを変更せずにデバッグを続行します。<br /><br /> または<br /><br /> デバッグを停止して変更を再適用した後、デバッグを再開します。|1009、1011。このカテゴリのエラー メッセージと警告メッセージの一覧については、「[元に戻すか停止するメッセージ](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_UndoOrStopMessages)」を参照してください。|  
|デバッグを続行します。  最初にそのコードに達したときは変更は無視されますが、以降の呼び出しでは変更が適用されます。|2001, 2002, 2004.  このカテゴリのエラー メッセージと警告メッセージの一覧については、「[次の呼び出しで適用するメッセージ](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_ApplyAtNextCallMessages)」を参照してください。|  
|ブレークポイントのリセット、[!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)] の現在のバージョンを使用したモジュールのリビルドなど、別のアクションを実行します。|2007, 2008.  このカテゴリのエラー メッセージと警告メッセージの一覧については、「[別のアクションが必要なメッセージ](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_OtherActionRequiredMessages)」を参照してください。|  
  
##  <a name="BKMK_RestartDebuggingMessages"></a> デバッグを再起動するメッセージ  
 次のエラー メッセージを解決するには、現在のデバッグ セッションを停止し、編集を再適用して、デバッグ セッションを再起動する必要があります。  
  
|||  
|-|-|  
|1001|シンボルに対するサンクの更新ができません: *symbol* \(loc: *location*, サンク: *address*\)|  
|1002|データ シンボルが変更されています: symbol \(*symbol*\)|  
|1003|新しい関数に対してサンクの割り当てができません: *function*|  
|1004|型パッキングの PDB を開けません: *pdb* \(pdb\)|  
|1005|シンボルが名称変更、削除または変更されています: *symbol*|  
|1006|グローバルまたは静的変数は、追加、名前の変更、削除されました。またはデータ型か初期化子が変更されました: *symbol* \(参照元: *module*\)|  
|1007|シンボルは定義されていません: *symbol* \(参照元: *module*\)|  
|1008|エディット中に読み込まれたオブジェクトによって要求されたランタイム初期化処理を実行できません: *module*|  
|1010|グローバルまたは静的変数が追加されました: *variable referenced in file*|  
|1013|デバッガーはコード変更を適用中にメモリ不足になりました。|  
|2003|コード位置の変更により例外や変数のデストラクション エラーが起きる可能性があります: *function*|  
|2005|新しいソースはコードに変更を与えます。  デバッガーの行番号情報に対する影響があるかもしれません: 関数 \(*function*\)|  
  
##  <a name="BKMK_UndoOrStopMessages"></a> 元に戻すか停止するメッセージ  
 次のエラー メッセージは、現在のデバッグ セッションを停止し、編集を再適用して、デバッグ セッションを再起動することで解決できます。  
  
-   \[編集\] メニューの \[元に戻す\] をクリックします。  デバッグは再開できますが、編集は適用されません。  
  
     または  
  
-   デバッグを停止して編集を再適用した後、デバッグを再開します。  
  
|||  
|-|-|  
|1009|グローバルまたは静的変数が削除されました: *variable referenced in file*|  
|1011|グローバルまたは静的変数が変更されました: *variable referenced in file*|  
  
##  <a name="BKMK_ApplyAtNextCallMessages"></a> 次の呼び出しで適用するメッセージ  
 次のいずれかの警告メッセージが表示された場合、デバッグ セッションを続行できます。  編集後に初めてこのコードが呼び出されたときには、編集は適用されせん。それ以降のこのコードの呼び出しにはすべて、編集が適用されます。  
  
|||  
|-|-|  
|2001|ローカル変数が見つからないか、または変数のデータ型が変更されました: シンボル \(*symbol*\)|  
|2002|削除された変数または新しいローカル変数にはコンストラクション\/デストラクションが必要です: シンボル \(*symbol*\)|  
|2004|既に定義されている名前でローカル変数を追加、削除することはできません: シンボル \(*symbol*\)|  
  
##  <a name="BKMK_OtherActionRequiredMessages"></a> 別のアクションが必要なメッセージ  
 これらのメッセージを解決するために必要なアクションについては、メッセージ テキストの後で説明します。  
  
|||  
|-|-|  
|2007|逆アセンブル ウィンドウに設定したブレークポイントの中には移動できないものもあります。<br /><br /> この問題を解決するには、影響を受けるブレークポイントをリセットします。|  
|2008|モジュール *module* 内のファイル *file* のデバッグ シンボルを読み込めませんでした。<br /><br /> この問題を解決するには、[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] の現在のバージョンを使用して、指定されたモジュールをリビルドします。|  
  
## 参照  
 [エディット コンティニュ \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md)   
 [エディット コンティニュ](../debugger/edit-and-continue.md)