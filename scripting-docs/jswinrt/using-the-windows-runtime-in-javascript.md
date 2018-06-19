---
title: JavaScript での Windows ランタイムの使用 | Microsoft Docs
ms.custom: ''
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c81f5d83056ceb87987e263f09c0d5e5017dbb6f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571462"
---
# <a name="using-the-windows-runtime-in-javascript"></a>JavaScript での Windows ランタイムの使用
ユニバーサル Windows プラットフォーム (UWP) アプリを作成する場合、ネイティブ JavaScript オブジェクト、メソッド、プロパティを使用するのとほとんど同じように、Windows ランタイム クラス、メソッド、プロパティを使用できます。 このトピックでは、JavaScript の概要を説明し、JavaScript で Windows ランタイム API を使用する際の基本概念を説明するトピックへのリンクを記載します。リンク先のトピックでは、Windows ランタイム型の表現方法、非同期 Windows ランタイム メソッドを使用する方法、Windows ランタイム イベントをリッスンして処理する方法などを説明しています。  
  
 JavaScript のリファレンス ドキュメントについては、「[JavaScript 言語リファレンス](../javascript/javascript-language-reference.md)」を参照してください。  
  
> [!IMPORTANT]
>  Windows ランタイムの機能は Internet Explorer で実行されるアプリでは使用できません。  
  
## <a name="windows-runtime-reference-documentation"></a>Windows ランタイムのリファレンス ドキュメント  
 リファレンス ドキュメントについては、「[Windows ランタイム リファレンス](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx)」を参照してください。 コード例は、JavaScript だけでなく、C++、C#、および Visual Basic でも利用できます。  
  
## <a name="writing-windows-runtime-components-in-c-c-or-visual-basic"></a>C++、C#、または Visual Basic での Windows ランタイム コンポーネントの作成  
 JavaScript で利用できる Windows ランタイム コンポーネントの作成手順とガイドラインについては、「[C++ で Windows ランタイム コンポーネントを作成する](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)」および「[C# および Visual Basic での Windows ランタイム コンポーネントの作成](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)」を参照してください。  
  
## <a name="casing-conventions-with-windows-runtime-features"></a>Windows ランタイム機能の表記規則  
 JavaScript での Windows ランタイム機能の表記規則は、他の言語での表記規則とは少し異なります。  
  
-   名前空間とクラスは、Pascal 形式で表記されます。  
  
    ```JavaScript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   クラスのメンバー (メソッドとプロパティを含む) と構造および列挙体のメンバーは、Camel 形式で表記されます。  
  
    ```JavaScript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   イベント名は、小文字で表記されます。  
  
    ```JavaScript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## <a name="see-also"></a>関連項目  
 [Windows ランタイム API を使用する際の考慮事項](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [Windows ランタイムの非同期メソッドの使用](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [JavaScript での Windows ランタイム イベントの処理](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [Windows ランタイム型の JavaScript 表現](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [Windows ランタイムの DateTime および TimeSpan の JavaScript 投影](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)