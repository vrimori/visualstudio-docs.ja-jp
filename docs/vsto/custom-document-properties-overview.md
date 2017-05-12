---
title: "カスタム ドキュメント プロパティの概要"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "_AssemblyLocation プロパティ"
  - "_AssemblyName プロパティ"
  - "カスタム ドキュメント プロパティ"
  - "ドキュメント レベルのカスタマイズ [Visual Studio での Office 開発], カスタムのプロパティ"
  - "ドキュメント [Visual Studio での Office 開発], カスタムのプロパティ"
  - "Office ドキュメント [Visual Studio での Office 開発, カスタムのプロパティ"
ms.assetid: 9a215904-b760-4a49-93e8-a1a708ce0526
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# カスタム ドキュメント プロパティの概要
  ドキュメント レベルのプロジェクトをビルドすると、Visual Studio によってプロジェクト内のドキュメントに \_AssemblyLocation および \_AssemblyName という 2 つのカスタム プロパティが追加されます。  ユーザーがドキュメントを開くと、Microsoft Office アプリケーションがこの 2 つのカスタム ドキュメント プロパティをチェックします。  ドキュメントにこれらのプロパティが存在する場合は、アプリケーションが [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] を読み込み、そのランタイムによってカスタマイズが起動されます。  詳細については、「[Visual Studio の Office ソリューションのアーキテクチャ](../vsto/architecture-of-office-solutions-in-visual-studio.md)」を参照してください。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## \_AssemblyName  
 このプロパティには、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] の Office ソリューション ローダー コンポーネントのインターフェイスの CLSID が含まれています。  CLSID 値は 4E3C66D5\-58D4\-491E\-A7D4\-64AF99AF6E8B です。  この値は変更できません。  
  
## \_AssemblyLocation  
 このプロパティには、カスタマイズの配置マニフェストに関する詳細を示す文字列が含まれます。  マニフェストの詳細については、「[Office ソリューションにおけるアプリケーション マニフェストと配置マニフェスト](../vsto/application-and-deployment-manifests-in-office-solutions.md)」を参照してください。  
  
 \_AssemblyLocation プロパティの値は、ソリューションの配置方法によって形式が異なります。  
  
-   ソリューションを、Web サイト、UNC パス、CD ドライブ、または USB ドライブからのインストールを前提として発行した場合、\_AssemblyLocation プロパティの形式は *DeploymentManifestPath*|*SolutionID* となります。  たとえば、次のような文字列になります。  
  
     file:\/\/deployserver\/MyShare\/ExcelWorkbook1.vsto|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9  
  
-   ソリューションを Visual Studio から実行またはデバッグする場合、\_AssemblyLocation プロパティの形式は *DeploymentManifestName*|*SolutionID*|vstolocal となります。  たとえば、次のような文字列になります。  
  
     ExcelWorkbook1.vsto|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9|vstolocal  
  
 *SolutionID* はソリューションを特定するために [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] が使用する GUID です。  *SolutionID* は自動的にプロジェクトをビルドするときに生成されます。**vstolocal** の用語は [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] にアセンブリをドキュメントと同じフォルダーから読み込まれることを示します。  
  
## 参照  
 [Visual Studio の Office ソリューションのアーキテクチャ](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)   
 [Office ソリューションにおけるアプリケーション マニフェストと配置マニフェスト](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [方法: ClickOnce を使用して Office ソリューションを公開する](http://msdn.microsoft.com/ja-jp/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [方法 : カスタム ドキュメント プロパティを作成および変更する](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  