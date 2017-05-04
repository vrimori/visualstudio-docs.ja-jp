---
title: "&lt;entryPoint&gt; 要素 (Visual Studio での Office 開発) | Microsoft Docs"
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
  - "アプリケーション マニフェスト [Visual Studio での Office 開発]、<entryPoint> 要素"
  - "<entryPoint> 要素"
  - "entryPoint 要素"
ms.assetid: 0c9d22d0-0852-4260-89c6-b83f24e48793
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;entryPoint&gt; 要素 (Visual Studio での Office 開発)
  `vstav3`  名前空間の各 `entryPoint` 要素によって、この [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] アプリケーションのインストール時に実行する必要のあるカスタマイズ アセンブリを指定します。  
  
## 構文  
  
```  
<entryPoint class>  
    <assemblyIdentity />  
</entryPoint>  
```  
  
## 要素と属性  
 `entryPoint` 要素は必須です。この要素は `vstav3`  名前空間にあります。  
  
 `entryPoint` 要素ごとに、1 つのカスタマイズ アセンブリのみを含めることができます。 アプリケーション マニフェストには、複数の `entryPoint` 要素を定義できます。  
  
 `entryPoint` 要素には、次の属性があります。  
  
|属性|説明|  
|--------|--------|  
|`class`|必須です。 実行するカスタマイズ アセンブリを指定します。 この属性の構文は、*NamespaceName.ClassName*です。|  
  
 `entryPoint` には、次の要素があります。  
  
### assemblyIdentity  
 必ず指定します。`vstav3`  名前空間の `assemblyIdentity` 要素は、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] アプリケーション マニフェストで定義された既存の `assemblyIdentity` 要素を参照します。  
  
 `assemblyIdentity` とその属性の役割は、[&#60;assemblyIdentity&#62; 要素 &#40;ClickOnce アプリケーション&#41;](../Topic/%3CassemblyIdentity%3E%20Element%20(ClickOnce%20Application).md) で定義されます。  
  
## ドキュメント レベルのカスタマイズの例  
  
### 説明  
 次のコード例は、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] を使用して配置するドキュメント レベルの Office ソリューションに対するアプリケーション マニフェストの `entryPoint` 要素を示しています。 このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」に記載されている例の一部を抜粋したものです。  
  
### コード  
  
```  
<vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint>  
```  
  
## VSTO アドインの例  
  
### 説明  
 次のコード例は、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] を使用して配置するアプリケーション レベルの Office ソリューションに対するアプリケーション マニフェストの `entryPoint` 要素を示しています。 このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」に記載されている例の一部を抜粋したものです。  
  
### コード  
  
```  
<vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint>  
```  
  
## 参照  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)  
  
  