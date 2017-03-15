---
title: "例外のトラブルシューティング : System.IO.FileLoadException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "FileLoadException クラス"
ms.assetid: 6b4519e3-4d29-4031-8aec-c2735b4ee16d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.IO.FileLoadException
<xref:System.IO.FileLoadException> 例外は、マネージ アセンブリが見つかっても読み込むことができないときにスローされます。  
  
## 関連するヒント  
 **ファイルが有効な .NET Framework アセンブリであることを確認します。**  
 この例外は、ファイルが有効な .NET Framework アセンブリではない場合にスローされます。 詳細については、「<xref:System.Reflection.Assembly>」を参照してください。  
  
 **アセンブリまたはモジュールが、2 つの異なる証拠を使用して 2 回読み込まれていないことを確認します。**  
 証拠とは、セキュリティ ポリシーがアクセス許可を決定するときに使用する一連の情報 \(コードにどのようなアクセス許可を付与できるかなど\) のことです。 詳細については、「<xref:System.EnterpriseServices.Internal.Publish.GacRemove%2A>」および「<xref:System.Reflection.Assembly.Evidence%2A>」を参照してください。  
  
 **RegisterAssembly メソッドまたは UnregisterAssembly メソッドを使用している場合は、アセンブリ名が MAX\_PATH の文字数を超えていないことを確認します。**  
 アセンブリ名には MAX\_PATH を超える文字数を指定できません。 詳細については、<xref:System.EnterpriseServices.Internal.IComSoapPublisher.RegisterAssembly%2A> および <xref:System.EnterpriseServices.Internal.IComSoapPublisher.UnRegisterAssembly%2A> を参照してください。  
  
 **サテライト アセンブリを読み込んでいる場合、指定した CultureInfo がファイルの CultureInfo に一致していることを確認します。**  
 サテライト アセンブリには、ローカライズできない実行可能コードを含むローカライズ済みリソースや、既定のカルチャまたはニュートラル カルチャとして機能する単一カルチャ用のリソースが含まれています。 詳細については、「<xref:System.Reflection.Assembly.GetSatelliteAssembly%2A>」を参照してください。  
  
## 参照  
 <xref:System.IO.FileLoadException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)