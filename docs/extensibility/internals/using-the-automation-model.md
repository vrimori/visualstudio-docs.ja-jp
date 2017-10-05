---
title: "オートメーション モデルを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 15
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 82a9c2068bdd3e234bcc53ffa870ca289289d690
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="using-the-automation-model"></a>オートメーション モデルを使用します。
オートメーションに VSPackage を接続した後に取得できますプロパティとメソッドを呼び出して、<xref:EnvDTE.DTEClass.GetObject%2A>メソッドを<xref:EnvDTE._DTE>オブジェクトを取得するオブジェクトを表す文字列を渡します。  
  
## <a name="obtaining-project-objects"></a>プロジェクトのオブジェクトを取得します。  
 オートメーション コンシューマーを取得する方法、プロジェクトのオートメーション オブジェクトを示す 2 つのコード例を次に示します。 DTE オブジェクトを取得する方法については、次を参照してください。[する方法: DTE および DTE2 オブジェクトへの参照の取得](http://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4)です。  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp  
void DoAutomation(void)  
{  
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.  
    pMyPkg = pDTE->GetObject("AcmeProjects");   
  
   // The '=' performs a Query Interface.  
   // Assumes pDTE is already available as a global.  
   // Use pMyPkg to access your projects object's properties and methods.  
}  
  
```  
  
 この時点では、階層モデル下へ移動する特定の VSPackage の一部である標準プロジェクト オブジェクトを使用できます。  
  
 次のコード例は、カスタム プロジェクトの種類のプロパティをカスタム オブジェクトを取得する方法を示します。。  
  
```vb  
Dim MyPrj As Project  
Dim MyPrjItem As ProjectItem  
Dim objMyObject as MyExtendedObject  
  
MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project  
objMyObject = MyPrj.Object 'You call .Object to get to special Project  
                           'implementation  
objMyObject.MySpecialMethodOrProperty  
```  
  
 次のコードがすべてのプロパティの名前を一覧表示、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境**全般** オプションを選択、**ツール**メニュー。  
  
```vb  
dim objDTE  
dim objEnv  
set objDTE = CreateObject("VisualStudio.DTE")  
set objEnv = objDTE.Properties("Environment", "General")  
for each obj in ObjEnv  
MsgBox obj.Name  
Next  
  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:EnvDTE.DTEClass.GetObject%2A>
