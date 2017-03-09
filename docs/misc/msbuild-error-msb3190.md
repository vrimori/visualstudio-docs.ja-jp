---
title: "MSBuild エラー MSB3190 | Microsoft Docs"
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
  - "GenerateManifest.InvalidRequestedExecutionLevel"
helpviewer_keywords: 
  - "MSB3190"
ms.assetid: 45b45688-9345-45db-adc8-3e200f1c17eb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3190
**MSB3190: ClickOnce では、要求の実行レベル '\<level\>' はサポートされていません。**  
  
 このエラーは、Windows Vista を実行しているコンピューターで、アプリケーションの埋め込みユーザー アカウント制御 \(UAC: User Account Control\) マニフェストに、管理資格情報を使用して ClickOnce アプリケーションを実行するように指定している場合に生成されます。  ClickOnce および登録を必要としない COM には、アプリケーションを現在のユーザーとして実行するように指定した外部マニフェストが必要です。  
  
 ClickOnce では、`requireAdministrator` または `highestAvailable` の実行レベルは使用できません。  これらのレベルのいずれかを指定すると、このエラーが返されます。  ClickOnce では `asInvoker` を使用する必要がありますが、`<requestedExecutionLevel>` ノードを記述しない場合にも対応しています。これにより、ファイルとレジストリの仮想化が指定されます。これはマニフェストを生成しない場合に該当し、下位互換性のために用意されている動作です。  
  
> [!NOTE]
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### このエラーを解決するには  
  
-   アプリケーションを現在のユーザー \(`asInvoker`\) として実行するように指定した外部 UAC マニフェスト \(アプリケーション マニフェスト\) を生成します。  
  
     Visual C\# プロジェクトでは、プロジェクト デザイナーの **\[アプリケーション\]** ページに移動し、**\[マニフェスト\]** の一覧の **\[Properties\\app.manifest\]** をクリックします。  詳細については、「[\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(C\#\)](../Topic/Application%20Page,%20Project%20Designer%20\(C%23\).md)」を参照してください。  
  
     Visual Basic プロジェクトでは、プロジェクト デザイナーの **\[アプリケーション\]** ページに移動し、**\[UAC 設定の表示\]** ボタンをクリックします。  アプリケーション マニフェストが編集用に開きます。  マニフェストの次のタグを以下のように編集します。  
  
    ```  
    <requestedExecutionLevel level="asInvoker" />  
    ```  
  
     詳細については、「[\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](../Topic/Application%20Page,%20Project%20Designer%20\(Visual%20Basic\).md)」を参照してください。  
  
-   UAC マニフェストを生成する方法および実行レベルを指定する方法の詳細については、「[Windows Vista の ClickOnce 配置](../deployment/clickonce-deployment-on-windows-vista.md)」を参照してください。  
  
## 参照  
 [\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(C\#\)](../Topic/Application%20Page,%20Project%20Designer%20\(C%23\).md)   
 [\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](../Topic/Application%20Page,%20Project%20Designer%20\(Visual%20Basic\).md)   
 [Windows Vista の ClickOnce 配置](../deployment/clickonce-deployment-on-windows-vista.md)