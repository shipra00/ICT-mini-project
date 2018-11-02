# ICT-mini-project

def distance_a_b(location_of_a, location_of_b):   #the locations are tuples
  distance=((location_of_a[0]-location_of_b[0])**2+(location_of_a[1]-location_of_b[1])**2)**(0.5)  
  return distance
  
def sort_distance(canteen_distance):   #canteen distance is a list
  list_len = len(canteen_distance)

    # base case
  if list_len < 2:
    return canteen_distance
  left_list = canteen_distance[:list_len // 2]   # //
  right_list = canteen_distance[list_len // 2:]  # "//" to force division

    # merge sort left and right list recursively
  left_list = sort_distance(left_list)
  right_list = sort_distance(right_list) 
  return merge(left_list, right_list)
  
def merge(left_list, right_list):
  result_list = []

    # while left and right list has elements
  while left_list and right_list:
      if left_list[0] < right_list[0]:
        result_list.append(left_list[0])
        left_list.pop(0)
      else:
        result_list.append(right_list[0])
        right_list.pop(0)

    #left list still contain elements. Append its contents to end of the result list
  if left_list:
    result_list.extend(left_list)
  else:
   #right list still contain elements. Append its contents to end of the result list
    result_list.extend(right_list)
    
  return result_list
  
