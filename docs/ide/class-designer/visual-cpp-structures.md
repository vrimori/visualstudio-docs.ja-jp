---
title: クラス デザイナーの Visual C++ 構造体
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 6daa85e9f8a3ea6f5fe68808cd46fc4414f77c17
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966362"
---
# <a name="visual-c-structures-in-class-designer"></a>クラス デザイナーの Visual C++ 構造体

**クラス デザイナー**は、C++ の構造体をサポートしています。これは、`struct` キーワードを使用して宣言されます。 例を次に示します。

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

`struct` 型の使用法の詳細については、「[struct](/cpp/cpp/struct-cpp)」を参照してください。

クラス ダイアグラムにおける C++ 構造体の図形の形状と動作はクラスの図形に似ていますが、ラベルが **[Struct]** である点と、角が丸くなく直角である点が異なります。

|コード要素|クラス デザイナー ビュー|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> 構造体|

## <a name="see-also"></a>関連項目

- [Visual C++ コードの使用](working-with-visual-cpp-code.md)
- [クラスと構造体](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)