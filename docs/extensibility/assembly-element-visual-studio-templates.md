---
title: "Assembly 要素 (Visual Studio テンプレート) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Assembly"
helpviewer_keywords: 
  - "Assembly 要素 [Visual Studio テンプレート]"
  - "<Assembly> 要素 [Visual Studio テンプレート]"
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Assembly 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

アセンブリに関する情報を指定します。テンプレートがプロジェクトへアセンブリ参照を追加するときに、テンプレートによって使用されます。  
  
## 構文  
  
```  
<Assembly> AssemblyName </Assembly>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[参照](../extensibility/reference-element-visual-studio-templates.md)|プロジェクトにアイテムを追加するときに、追加するアセンブリ参照を指定します。|  
  
## テキスト値  
 テキスト値が必要です。  
  
 項目テンプレートがインスタンス化されるときにプロジェクトに追加されるアセンブリを指定します。  このアセンブリ名は、次のいずれかの方法で指定する必要があります。  
  
-   完全なアセンブリ名を指定します。  以下はその例です。  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   簡易テキスト参照を指定します。  以下はその例です。  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## 解説  
 `Assembly` は、`Reference` に必須の子要素です。  
  
 `Reference` 要素、`References,` 要素、および `Assembly` 要素は、`Type` 属性に `Item` の値が付いている .vstemplate ファイルだけで使用できます。  
  
## 使用例  
 項目テンプレートの `TemplateContent` 要素の例を次に示します。  この XML では、System.dll アセンブリおよび System.Data.dll アセンブリへの参照を追加します。  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## 参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)