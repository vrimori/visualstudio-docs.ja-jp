---
title: "&lt;description&gt; 要素 (ClickOnce 配置) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#description"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<description> 要素 [ClickOnce 配置マニフェスト]"
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# &lt;description&gt; 要素 (ClickOnce 配置)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[スタート\] メニューの項目 \(シェルのプレゼンス\) とコントロール パネルの **\[プログラムの追加と削除\]** の項目を作成するために使用されるアプリケーション情報を識別します。  
  
## 構文  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## 要素と属性  
 `description` 要素は必須です。この要素は `urn:schemas-microsoft-com:asm.v1` 名前空間にあります。  子要素を含まず、次の属性を持ちます。  
  
|属性|Description|  
|--------|-----------------|  
|`publisher`|必ず指定します。  インストール用の配置を設定するときに、Windows の **\[スタート\]** メニューとコントロール パネルの **\[プログラムの追加と削除\]** の項目にアイコンを追加するために使用される企業名を指定します。|  
|`product`|必ず指定します。  完全な製品名を指定します。  この名前は、Windows の **\[スタート\]** メニューにインストールされるアイコンのタイトルとして使用されます。|  
|`suiteName`|省略可能です。  Windows の **\[スタート\]** メニューの `publisher` フォルダー内のサブフォルダーを指定します。|  
|`supportUrl`|省略可能です。  コントロール パネルの **\[プログラムの追加と削除\]** 項目に表示されるサポート URL を指定します。  インストール用として配置を設定する場合、アプリケーション サポート用に Windows の **\[スタート\]** メニューにもこの URL へのショート カットが作成されます。|  
  
## 解説  
 description 要素は、すべての配置構成で必須です。  
  
## 使用例  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置マニフェスト内の `description` 要素を次のコード例に示します。  このコード例は、「[ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)」で示されている例の一部の抜粋です。  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## 参照  
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)