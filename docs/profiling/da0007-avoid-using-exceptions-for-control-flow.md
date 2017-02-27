---
title: "DA0007: 制御フローでの例外の使用を避けてください | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAExceptionsThrown"
  - "vs.performance.7"
  - "vs.performance.rules.DA0007"
  - "vs.performance.DA0007"
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# DA0007: 制御フローでの例外の使用を避けてください
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0007|  
|分類|.NET Framework の使用|  
|プロファイル方法|すべて|  
|メッセージ|多数の例外が継続してスローされています。  プログラム ロジックで例外の使用を減らすことを検討してください。|  
|メッセージの種類|警告|  
  
 サンプリング、.NET メモリ、またはリソース競合メソッドを使用してプロファイリングを行うときは、この規則を呼び出すためのサンプルを少なくとも 25 個収集する必要があります。  
  
## 原因  
 .NET Framework 例外ハンドラーの多くの部分がプロファイル データで呼び出されました。  他の制御フロー ロジックを使用して、スローされる例外の数を減らすことを検討してください。  
  
## 規則の説明  
 例外ハンドラーを使用して、プログラム実行を中断するエラーやその他のイベントをキャッチするのは良い方法ですが、通常のプログラム実行ロジックの一部として例外ハンドラーを使用すると負荷が高くなる可能性があるため、避けてください。  ほとんどの場合、例外は、あまり発生することのない、予期しない状況に対してのみ使用する必要があります。  値を返すときに通常のプログラム フローの一部として例外を使用しないでください。  多くの場合、値を検証し、条件付きロジックを使用して問題の原因となっているステートメントの実行を中断することで、例外の発生を抑えることができます。  
  
 詳細については MSDN の **Microsoft Patterns and Practices** [例外管理](http://go.microsoft.com/fwlink/?LinkID=177825) ライブラリ **Improving .NET Application Performance and Scalability** ボリュームの **Chapter 5 — Improving Managed Code Performance** のセクションを参照します。  
  
## 警告の調査方法  
 \[エラー一覧\] ウィンドウに表示されたメッセージをダブルクリックして、\[マーク\] ビューに移動します。  **.NET CLR Exceptions\(@ProcessInstance\)\\\# of Exceps Thrown \/ sec** の測定値が含まれる列を見つけます。  例外処理の頻度が他よりも高い特定のプログラム実行フェーズがあるかどうかを確認します。  サンプリング プロファイルを使用して、頻繁な例外を生成する throw ステートメントおよび try\/catch ブロックを識別してください。  必要に応じて、ロジックを catch ブロックに追加すると、最も頻繁に処理されている例外を見分けることができます。  可能な場合は、頻繁に実行される throw ステートメントまたは catch ブロックを、簡単なフロー制御ロジックまたは検証コードと置き換えてください。  
  
 たとえば、アプリケーションが DivideByZeroException 例外を頻繁に処理している場合、ロジックをプログラムに追加して値が 0 の分母をチェックすると、アプリケーションのパフォーマンスが向上します。