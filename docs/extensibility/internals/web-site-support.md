---
title: "Web サイトのサポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 636cbee868bb53be2d0ef85bd309459570eb84c0
ms.lasthandoff: 02/22/2017

---
# <a name="web-site-support"></a>Web サイトのサポート
Web サイト プロジェクト システムは、Web プロジェクトを作成するためにプロジェクト システムです。 Web プロジェクトは、Web アプリケーションを作成します。 Web サイト プロジェクトでは、コードが関連付けられている各 Web ページの&1; つの実行可能ファイルを生成します。 その他の実行可能ファイルは/App_Code フォルダー内のソース コード ファイルから生成されます。  
  
 Web サイト プロジェクト システムを作成するには、既存のプロジェクト システムへのテンプレートと登録の属性を追加します。 これらの属性のいずれかには、言語の IntelliSense プロバイダーを指定します。 IntelliSense のプロバイダーの実装では、参照を処理し、スマート Web ページがキャッシュされていないことを要求するときに、言語コンパイラを呼び出します。  
  
 Web ページをコンパイルするために使用する言語コンパイラに登録する必要があります[!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]します。 使用することができます、 [\<コンパイラ > 要素](http://msdn.microsoft.com/Library/7a151659-b803-4c27-b5ce-1c4aa0d5a823)を次の例に示すように、コンパイラを登録する Web.config ファイルで。  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Web サイト テンプレートをサポート](../../extensibility/internals/web-site-support-templates.md)  
 新しい Web サイト プロジェクトと関連付けられているアイテムの作成に使用できるテンプレートが一覧表示します。  
  
 [Web サイトのサポートの属性](../../extensibility/internals/web-site-support-attributes.md)  
 Web サイト プロジェクトを接続している登録属性を表示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]と[!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]です。  
  
## <a name="related-sections"></a>関連項目  
 [Web プロジェクト](../../extensibility/internals/web-projects.md)  
 Web プロジェクト、Web サイト プロジェクトと Web アプリケーション プロジェクトの&2; 種類の概要を示します。
