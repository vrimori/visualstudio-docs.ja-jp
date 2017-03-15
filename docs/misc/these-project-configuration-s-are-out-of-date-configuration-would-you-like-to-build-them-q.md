---
title: "These project configuration(s) are out of date: &lt;configuration&gt;. (これらのプロジェクト構成は最新ではありません: &lt;configuration&gt;。) ビルドしますか? | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Message.BuildOutOfDateProjects"
ms.assetid: d0711f3b-3a2e-4247-afad-9e6468f9df96
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# These project configuration(s) are out of date: &lt;configuration&gt;. (これらのプロジェクト構成は最新ではありません: &lt;configuration&gt;。) ビルドしますか?
Visual Studio プロジェクトの編集中、またはソリューション エクスプローラーでプロジェクトを選択している状態のときに、\[開始\] \(F5 キー\) または \[デバッグなしで開始\] \(Ctrl \+ F5 キー\) でプロジェクトを実行しようとしました。 1 つまたは複数のプロジェクトでは、プロジェクトが最後のビルド時以降に変更されている場合でもリビルドせずにデバッグできます。  
  
 これは、リビルドしなくてもデバッグできるプロジェクトをリビルドするかどうかを統合開発環境 \(IDE\) が確認しているメッセージです。  
  
### 対処方法  
  
-   メッセージの下部にあるボタンの 1 つをクリックします。 次のオプションがあります。  
  
|用語|定義|  
|--------|--------|  
|**はい**|最新でないプロジェクトをリビルドします。 つまり、次の処理が行われます。<br /><br /> -   まだビルドされていないプロジェクトの場合はビルドされます。<br />-   最後のビルド時以降に変更されているプロジェクトの場合はリビルドされます。<br />-   プロジェクトのデバッグが行われるか、またはデバッグなしで実行が開始されます。|  
|**いいえ**|最新でないプロジェクトのうち、デバッグの前にリビルドが必要なものだけをリビルドします。 つまり、次の処理が行われます。<br /><br /> -   リビルドしなくてもデバッグできるプロジェクト \(たとえば、Visual C\+\+ MFC アプリケーション プロジェクト\) の場合はリビルドされません。<br />-   デバッグの前にリビルドが必要なプロジェクト \(たとえば、Visual Basic プロジェクト\) の場合はリビルドされます。<br />-   プロジェクトのデバッグが行われるか、またはデバッグなしで実行が開始されます。|  
|**キャンセル**|現在の操作を中止します。 プロジェクトのビルド、実行、またはデバッグは行われません。|  
  
## 参照  
 [&#91;構成マネージャー&#93; ダイアログ ボックス](http://msdn.microsoft.com/ja-jp/fa182dca-282e-4ae5-bf37-e155344ca18b)   
 [How to: Create Solution and Project Build Configurations](../Topic/How%20to:%20Create%20Solution%20and%20Project%20Build%20Configurations.md)   
 [方法 : プロジェクトの依存関係を作成および削除する](../Topic/How%20to:%20Create%20and%20Remove%20Project%20Dependencies.md)   
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/ja-jp/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Project Dependencies, Common Properties, Solution Property Pages Dialog Box](http://msdn.microsoft.com/ja-jp/2ba638fc-719c-4a79-b166-3455a4374e31)   
 [Visual Studio でのアプリケーションのビルド](../ide/compiling-and-building-in-visual-studio.md)   
 [ビルド構成について](../ide/understanding-build-configurations.md)   
 [NIB: コンテナーとしてのプロジェクト](http://msdn.microsoft.com/ja-jp/87d40f63-f487-4767-8963-64beec27ba1b)   
 [NIB: プロジェクトにおける項目の管理](http://msdn.microsoft.com/ja-jp/762e606b-7f44-4b66-97a1-e30a703654a0)