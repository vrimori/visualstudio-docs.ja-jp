---
title: "Cannot find custom tool &#39;custom tool&#39; on this system | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_instantiate_generator1"
ms.assetid: 51fe9bec-b8bc-4a4c-94aa-15a1f7cc8b6b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Cannot find custom tool &#39;custom tool&#39; on this system
プロジェクト システムがカスタム ツールを作成できませんでした。  プロジェクト システムによってインスタンスが作成されないため、要求されたカスタム ツールは実行されません。  カスタム ツールが正しくインストールおよび登録されるようにしてください。  
  
 このエラーは、特定のファイルの `CustomTool` プロパティに無効なカスタム ツールの名前を指定することによって発生する可能性があります。  プロジェクト ファイル \(.vbproj\/.csproj\) が編集されたために、`CustomTool` プロパティの値が無効になった可能性もあります。  または、別のコンピューターで開発されたプロジェクトにカスタム ツールが含まれているが、そのプロジェクトが使用されているコンピューターにカスタム ツールがインストールされていない可能性もあります。  `CustomTool` プロパティの詳細については、「[File Properties](http://msdn.microsoft.com/ja-jp/013c4aed-08d6-4dce-a124-ca807ca08959)」を参照してください。  
  
 このエラーは、カスタム ツールの [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md) でエラーが発生した場合にも発生します。  たとえば、登録が行われていないか、必要な DLL が見つからない可能性があります。  
  
## 参照  
 [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)