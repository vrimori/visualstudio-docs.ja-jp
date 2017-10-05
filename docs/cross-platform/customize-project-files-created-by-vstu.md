---
title: "VSTU によって作成されるプロジェクト ファイルのカスタマイズ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
caps.latest.revision: 2
author: ghogen
ms.author: ghogen
manager: ghogen
translation.priority.ht:
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
ms.translationtype: HT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 804b3f885b78f860b3c48a31be60ecf2ecb12303
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="customize-project-files-created-by-vstu"></a>VSTU によって作成されるプロジェクト ファイルのカスタマイズ
Visual Studio Tools for Unity は、プロジェクト ファイルの生成時に Unity スタイルのコールバックを提供します。 `VisualStudioIntegration.ProjectFileGeneration` イベントに登録し、プロジェクト ファイルが再生成されるたびに、それを変更します。  
  
## <a name="demonstrates"></a>使用例  
 Visual Studio Tools for Unity によって生成された Visual Studio プロジェクト ファイルをカスタマイズする方法について示します。  
  
## <a name="example"></a>例  
  
```csharp  
using System;  
using System.IO;  
using System.Linq;  
using System.Text;  
using System.Xml.Linq;  
  
using UnityEngine;  
using UnityEditor;  
  
using SyntaxTree.VisualStudio.Unity.Bridge;  
  
[InitializeOnLoad]  
public class ProjectFileHook  
{  
    // necessary for XLinq to save the xml project file in utf8  
    class Utf8StringWriter : StringWriter  
    {  
        public override Encoding Encoding  
        {  
            get { return Encoding.UTF8; }  
        }  
    }  
  
    static ProjectFileHook()  
    {  
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>  
        {  
            // parse the document and make some changes  
            var document = XDocument.Parse(content);  
            document.Root.Add(new XComment("FIX ME"));  
  
            // save the changes using the Utf8StringWriter  
            var str = new Utf8StringWriter();  
            document.Save(str);  
  
            return str.ToString();  
        };  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [例: ログのコールバック](../cross-platform/share-the-unity-log-callback-with-vstu.md)
